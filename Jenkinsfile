node('test-machine') {      
//Defined the workspace while creating the node
def workspace="/builds/workspace"
def LOCALREPO_VC_DIR="challenges"
ws("${workspace}"){
	stage('Clone the repo'){
	sh"""
	if [ ! -d $LOCALREPO_VC_DIR ]
        then
		git clone  git@github.com:kavitha091/challenges.git
	else
		cd $LOCALREPO_VC_DIR
		git pull
	fi
	"""
	
	}
	
	stage('Deploy the image'){
	sh"""
	cd "${workspace}/challenges/ci-cd-pipeline"
	sudo docker build -t dockerfile .
	sudo docker run -dp 7026:8000 dockerfile
	sudo docker ps -a
	"""
	}
	
	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerid')
	}
	
	
	stage('Push the image to docker hub'){
	    ws("${workspace}/challenges/ci-cd-pipeline"){
		Image = docker.build( 'kavitha91/kavitha-hub','.')	
	    docker.withRegistry('https://registry-1.docker.io/v2/', 'dockerid') {
            Image.push()
        }
	    }
	
	}
	stage('Clean up'){
	sh"""
	rm -rf "${workspace}/challenges"
	"""
		
	}
}
}

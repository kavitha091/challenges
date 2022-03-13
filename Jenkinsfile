node('test-machine') {      
//Defined the workspace while creating the node
def workspace="/builds/workspace/"
def LOCALREPO_VC_DIR="challenges"
ws("${workspace}"){
	stage('Clone the repo'){
	sh""" 
	if [ ! -d $LOCALREPO_VC_DIR ]
        then
		git clone  git@github.com:kavitha091/challenges.git
	else
		cd $LOCALREPO_VC_DIR
		git pull"
	fi
	"""
	
	}
	stage('Deploy the image'){
	sh"""
	cd "${workspace}/challenges/ci-cd-pipeline"
	sudo docker build -t dockerfile .
	sudo docker run -dp 7005:8000 dockerfile
	sudo docker ps -a
	"""
	}
	stage('Push the image to docker hub'){
	cd "${workspace}/challenges/ci-cd-pipeline"
	sh"""
	sudo  docker login
	sudo docker build -t kavitha91/kavitha-hub .
	sudo docker push kavitha91/kavitha-hub:latest
	""" 
	}
	stage('Clean up'){
	sh"""
	rm -rf "${workspace}/challenges"
	"""	
	}
}
}

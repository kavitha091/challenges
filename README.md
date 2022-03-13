# challenges

# Issues faced:

1) I Installed Jenkins in my local machine. I was not able to add the webhook as  "http:localhost:8080" due to DNS issue.
2) Docker login was giving below error
```
docker login -u --password-stdin
Warning: failed to get default registry endpoint from daemon (Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.26/info: dial unix /var/run/docker.sock: connect: permission denied). Using system default: https://index.docker.io/v1/
Error: Cannot perform an interactive login from a non TTY device
```

# 1. Solution:

I had to install ngrok and follow the below steps:
run ngrok, command : ngrok http 8080
will give below output:
```
ngrok by @inconshreveable                                                                                                                                        
Session Status                online
Session Expires               1 hour, 17 minutes
Version                       2.3.40
Region                        United States (us)
Web Interface                 http://127.0.0.1:4040
Forwarding                    http://b23f-103-109-146-28.ngrok.io -> http://localhost:8080
Forwarding                    https://b23f-103-109-146-28.ngrok.io -> http://localhost:8080
Connections                   ttl     opn     rt1     rt5     p50     p90
                              30      0       0.00    0.00    5.04    5.47 
                                                                                                        
```
Copy "b23f-103-109-146-28.ngrok.io" and replace "localhost" request will be forwarded to localhost

# 2. solution

I had to use dockerregistry method to login to docker hub.

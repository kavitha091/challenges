# challenges

#Issues faced:

I Installed Jenkins in my local machine. I was not able to add the webhook as  "http:localhost:8080" due to DNS issue.

#Solution:

I had to install ngrok and follow the below steps:
run ngrok, command : ngrok http 8080
will give below output:
ngrok by @inconshreveable                                                                                                                                     (Ctrl+C to quit)                                                                                                                                                                              <!---<!--- 
Session Status                online                                                                                                                                          Session Expires               1 hour, 17 minutes                                                                                                                              Version                       2.3.40                                                                                                                                          Region                        United States (us)                                                                                                                              Web Interface                 http://127.0.0.1:4040                                                                                                                           Forwarding                    http://b23f-103-109-146-28.ngrok.io -> http://localhost:8080                                                                                    Forwarding                    https://b23f-103-109-146-28.ngrok.io -> http://localhost:8080                                                                                                                                                                                                                                                                 Connections                   ttl     opn     rt1     rt5     p50     p90                                                                                                                                   30      0       0.00    0.00    5.04    5.47                                                                                                                     
                                                                     
-->

Copy "b23f-103-109-146-28.ngrok.io" and replace "localhost" request will be forwarded to localhost

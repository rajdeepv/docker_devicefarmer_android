PoC for STF deployment on a single machine
===========
# Installation

* install docker
* install docker-compose
* clone this repo

# Usage
choose an IP your deployment should use, usually that will be the IP of your host.  
choose a secret to be used for inter-service authentication.  
Update the `.env` file accordingly

Run `docker-compose up -d --build` 

Create provider as
`sudo docker run --name docker_devicefarmer_android_provider -d --net=host --restart unless-stopped -p 7400-7700:7400-7700 -e "ZMQ_TCP_KEEPALIVE=1" -e "ZMQ_TCP_KEEPALIVE_IDLE=300" devicefarmer/stf:latest stf provider --name Samsung_J5_Vyuhuhol@automation11.d4 --connect-sub tcp://automation11.d4:7250 --connect-push tcp://automation11.d4:7270 --storage-url http://automation11.d4:8018/  --heartbeat-interval 10000 --screen-ws-url-pattern "ws://automation11.d4:7080/d/automation11/<%= serial %>/<%= publicPort %>/" --adb-port 9128 --min-port 7400 --max-port 7700 --screen-jpeg-quality 10`
`sudo docker run --name docker_devicefarmer_android_provider -d --net=host --restart unless-stopped -p 7400-7700:7400-7700 -e "ZMQ_TCP_KEEPALIVE=1" -e "ZMQ_TCP_KEEPALIVE_IDLE=300" devicefarmer/stf:latest stf provider --name Samsung_A40@automation3.d4 --connect-sub tcp://automation11.d4:7250 --connect-push tcp://automation11.d4:7270 --storage-url http://automation11.d4:8018/  --heartbeat-interval 10000 --screen-ws-url-pattern "ws://automation11.d4:7080/d/automation3/<%= serial %>/<%= publicPort %>/" --adb-port 9130 --min-port 7400 --max-port 7700 --screen-jpeg-quality 10`
`sudo docker run --name docker_devicefarmer_android_provider -d --net=host --restart unless-stopped -p 7400-7700:7400-7700 -e "ZMQ_TCP_KEEPALIVE=1" -e "ZMQ_TCP_KEEPALIVE_IDLE=300" devicefarmer/stf:latest stf provider --name Samsung_S7@automation2.d4 --connect-sub tcp://automation11.d4:7250 --connect-push tcp://automation11.d4:7270 --storage-url http://automation11.d4:8018/  --heartbeat-interval 10000 --screen-ws-url-pattern "ws://automation11.d4:7080/d/automation2/<%= serial %>/<%= publicPort %>/" --adb-port 9128 --min-port 7400 --max-port 7700 --screen-jpeg-quality 10`

Point your browser to the IP you chose,  
login by providing any username and valid e-mail.


A little write-up on this setup:  
https://medium.com/@nikosch86/getting-started-with-automated-in-house-testing-on-android-smartphones-using-stf-dafecee4a8ee  
If you clap it will make me happy :)

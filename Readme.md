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
`docker run --name docker_devicefarmer_android_provider --rm -d -p 7400-7700:7400-7700 devicefarmer/stf:latest stf provider --name shakti --connect-sub tcp://host.docker.internal:7250 --connect-push tcp://host.docker.internal:7270 --storage-url http://host.docker.internal:8018/ --public-ip 192.168.1.170 --heartbeat-interval 10000 --screen-ws-url-pattern "ws://192.168.1.170:7080/d/nuc/<%= serial %>/<%= publicPort %>/" --adb-host host.docker.internal --adb-port 5037 --min-port 7400 --max-port 7700 --allow-remote`

Point your browser to the IP you chose,  
login by providing any username and valid e-mail.


A little write-up on this setup:  
https://medium.com/@nikosch86/getting-started-with-automated-in-house-testing-on-android-smartphones-using-stf-dafecee4a8ee  
If you clap it will make me happy :)

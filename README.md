# mqtt.conf
#==set mqtt docker in local pc not in docker foler===
#=================docker-compose.yml=================
  mosquitto:
    image: eclipse-mosquitto
    ports:
      - 1883:1883
      - 8883:8883
    volumes:
      - /srv/mqtt/data:/mosquitto/data
      - /srv/mqtt/log:/mosquitto/log
      - /srv/mqtt/config:/mosquitto/config

#==============set conf folder=======================
#==============mosquitto.conf========================
#is not set up will go out the mqtt
persistence true
persistence_location /mosquitto/data

#see log file to see why it not work
log_dest file /mosquitto/log/mosquitto.log

#cant login not need username and password
allow_anonymous true

#mqtt port
listener 1883

#mqtt websocker port
listener 8883
protocol websockets
#===========================================
#========copy to /srv/mqtt/config========
mosquitto/config/mosquitto.conf


#========go into docker ,and set passwd and username========
mosquitto_passwd -c /mosquitto/config/pwfile user_name

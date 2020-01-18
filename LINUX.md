#### create folder
    mkdir folder-name
#### To read the file
    cat filenate
#### Server running in background
    screen
#### List out all running ports
    sudo lsof -i -P -n | grep LISTEN
#### Kill the port (Use any one)
    kill port - sudo fuser -k  3000/tcp
    sudo kill -9 $(sudo lsof -t -i:3000)


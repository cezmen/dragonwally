# dragonwally

PEOPLE IDENTIFICATION SYSTEM BASED ON STEREOSCOPIC COMPUTER VISION

This is the final "snapshot" of the DragonWally firmware, used during
the contest "Inventando o Futuro com DragonBoard 410c" ("Inventing the Future with DragonBoard 410c") 
organized by Embarcados and Qualcomm.

http://www.96boards.org/go/db410c-partnership-brazil/

Please, refer to the following URL for the DragonWally project details :

https://contest.embarcados.com.br/projetos/sistema-de-identificacao-de-pessoas-baseado-em-visao-computacional-estereoscopica/

[1] INSTALLATION

The user must choose an <install_dir> directory of the DragonBoard 410c.

To install, run the following commands :

    mkdir <install_dir>

    cd <install_dir>

    git clone https://github.com/cezmen/dragonwally/

    cd dragonwally

    tar -xvzf dragonwally-1.0.tar.gz

This will install the DragonWally project in the directory <install_dir>/dragonwally/dw


[2] DIRECTORY STRUCTURE

    DragonWally Sensor : <install_dir>/dragonwally/dw/dragonwallysensor

    DragonWally Admin  : <install_dir>/dragonwally/dw/dragonwallyadmin

    Utility Scripts    : <install_dir>/dragonwally/dw/utils


[3] MAIN SCRIPTS DESCRIPTION

    ACTIVATE CAMERAS :  <install_dir>/dragonwally/dw/utils/activate_two_cameras.sh

    RUN DRAGONWALLY SENSOR : <install_dir>/dragonwally/dw/dragonwallysensor/run_sensor.sh

    RUN DRAGONWALLY API : <install_dir>/dragonwally/dw/dragonwallyadmin/DragonWallyAPI/run_api.sh


[4] HARDWARE REQUIREMENTS 

    [4.1] DragonBoard 410c Kit (The DragonBoard 410c SBC, HDMI display, Keyboard and Mouse)
        https://www.arrow.com/en/products/dragonboard410c/arrow-development-tools
    
    [4.2] AIStarVision MIPI Adapter 2.0 with dual OV5645 Cameras
        http://www.96boards.org/product/mipi-adapter-mezzanine/
        https://github.com/Kevin-WSCU/96Boards-Camera
    
    [4.3] Logitech C270 Webcam
        https://www.logitech.com/product/hd-webcam-c270


[5] SOFTWARE REQUIREMENTS

    [5.1] Operating System : Linaro Debian 16.09
        http://builds.96boards.org/releases/dragonboard410c/linaro/debian/16.09/

    [5.2] AIStarVision Custom Boot Image for Dual Cameras
        https://github.com/Kevin-WSCU/96Boards-Camera/tree/master/Pre-built/Debian_16.09/StereoCamera/OV5645

        Using the "Fastboot Method", the user must replace the original "boot image" of Linaro Debian 16.09 
        with "boot-db410c.img" provided in the link above.

        Instructions of the "Fastboot Method" :
        http://www.96boards.org/documentation/ConsumerEdition/DragonBoard-410c/Installation/README.md


[6] AMAZON AWS CLOUD REQUIREMENTS

    [6.1] Install AWS Python packages:
        pip install awscli --upgrade --user
        sudo apt-get install awscli

    [6.2] Configure Amazon AWS Credentials:
    The user must provided an "access_key" and a "secret access key" provided by Amazon AWS.

        aws configure
        
            AWS Access Key ID [None]: <access_key_provided_by_user>
            AWS Secret Access Key [None]: <secret_access_key_provided_by_user>
            Default region name [None]: us-east-1
            Default output format [None]: json

    [6.3] Install AWS SDK for Python:
        pip install boto3 
 
[7] INSTALL THE FRONTEND

    sudo apt-get install lighttpd
    
    sudo service lighttpd start
    
    sudo cp -r <install_dir>/dragonwally/dw/dragonwallyadmin/DragonWallyFront/* /var/www/html/

    sudo rm /var/www/html/index.lighttpd.html
    
    sudo service lighttpd restart
    
 [8] RUN DRAGONWALLY
 
     [8.1] Activate Cameras
         <install_dir>/dragonwally/dw/utils/activate_two_cameras.sh
           
     [8.2] Run DragonWally Sensor
         <install_dir>/dragonwally/dw/dragonwallysensor/run_sensor.sh
 
     [8.3] Run DragonWally API
         <install_dir>/dragonwally/dw/dragonwallyadmin/DragonWallyAPI/run_api.sh
         
         
         

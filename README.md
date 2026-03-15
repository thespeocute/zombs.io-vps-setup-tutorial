## THIS IS A COMPLETE GUIDE ON SETTING UP A LINUX UBUNTU VPS FOR ZOMBS.IO 

## Before starting: 
   
   - You'll need an unbanned vps provider/location, these arnt too hard to find but let it be known alot of well known vps providers are banned due too other players using them.  
   
   - Any ssh program like windows powershell or putty.
   
   - Recommended specs for a single vps if youre planning on filling a server is atleast: 2 CPU cores, 3GB of memory and 30gb of ssd storage.
   
   - Choose a location near where zombs servers a located for less Ms.
   
   - YOU WILL NOT NEED TAMPERMONKEY ANYTHING FOR THIS.


### Getting started
   
   1. Open windows powershell or any other shh program and do this command: `ssh root@(YOUR-VPS'S-IP)`

   2. You will be prompted too type in your password, it wont show you typing it but just copy your password from your vps provider and paste it by right clicking in Powershell and press enter
   
   3. This should get you logged into your vps too set it up all from your own computer


## Main steps

   1. Download the mainx.zip file thats provided in this repository 
   
   2. On the ssh vps do these commands 

       - `sudo apt update && sudo apt upgrade -y`
       - `sudo apt install nodejs npm -y`
       - `node -v` (Should show v18 or higher)

   3. Create a directory and copy files

       - On the ssh Powershell window you have do these commands too make the file the zip will go into then go into that file

           - `mkdir ~/zombs`
           - `cd ~/zombs`
       
        - Go on your file explorer and go too where the file was downloaded, right click and copy the file path

       - Then open a new Powershell window and type this for each vps too upload the zip file too it

           - `scp -r (PATHWAY-THAT-YOu-COPIED) root@(YOUR-VPS-IP):/root/zombs/`
           
       - Back on the vps ssh install unzip

           - `sudo apt install unzip -y`

       - Then unzip it once its on there and unzip is downloaded

           - `unzip mainx.zip -d .`

       - Fix permissions

           - `chmod -R 755 .`

        - Move the files up

           - `cd /root/zombs`
           - `mv mainx/* .`
           - `mv mxyz/.* . 2>/dev/null || true`
           - `rmdir mxyz`
           - `ls -la` (should see server.js, public/, etc.)    

   4. Install pm2

       - On vps do these commands 

           - `sudo npm install -g pm2`
           - `pm2 startup`

       - Configure firewall    

           - `sudo apt install ufw -y`
           - `sudo ufw allow ssh`
           - `sudo ufw allow 80/tcp`
           - `sudo ufw allow 8080/tcp`
           - `sudo ufw enable`
           - `sudo ufw status`

   5.         





































   
                                      


# Zombs.io VPS Setup Guide 🚀

**Run your own Zombs.io proxy / session forwarder on a Linux VPS**

This guide helps you set up a lightweight proxy server on Ubuntu to host Zombs.io sessions with lower latency and more control.

## ✨ Features
- Simple Node.js + Express + WebSocket proxy
- PM2 process manager (auto-restart, logs)
- Basic UFW firewall protection
- No Tampermonkey / browser extension required

## 📋 Requirements
- **Unbanned VPS** (location close to Zombs.io servers for low ping)
- **Recommended specs** (for full server):  
  • 2+ CPU cores  
  • 3+ GB RAM  
  • 30+ GB SSD
- SSH client: Windows PowerShell, PuTTY, Terminal, etc.
- The `mainx.zip` file from this repository

**You do NOT need Tampermonkey or any browser scripts.**

## 🚀 Main steps

   1. Download the mainx.zip file thats provided in this repository 


   2. Ssh onto your vps(s) 

       - On your ssh program like powershell do `ssh root@(YOUR-VPS-IP)`

       - When prompted for a password enter it, it will not show you typing it but its there

       - That should allow you on your vps, if not its firewall issues on your provider side 
   
   
   3. On the ssh vps do these commands 

       - `sudo apt update && sudo apt upgrade -y`

       - `sudo apt install nodejs npm -y`

       - `node -v` (Should show v18 or higher)

   
   4. Create a directory and copy files

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
           
           - `mv mainx/.* . 2>/dev/null || true`

           - `rmdir mainx`
           
           - `ls -la` (should see server.js, public/, etc.)    

   
   5. Install pm2

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

   
   6. Install dependencies

       - `cd /root/zombs`
       
       - `npm init -y`

       - `npm install express ws bytebuffer`

   
   7. Edit index.js too have your ip on each vps

       - `cd /root/zombs`
      
       - `nano index.html`
 
       - While in nano do cntrl w and search for this line: `ws://(YOUR-VPS-IP):8080`

       - Change the (YOUR-VPS-IP) part too your vps's ip and leave the rest

       - Exit nano and save do cntrl o too save then press y and then cntrl x too exit nano    
   
  
   8. Start the pm2 server

       - `pm2 start /root/zombs/server.js --name zombs-proxy --cwd /root/zombs`

       - `pm2 save`  

   
   9. Check logs 
 
       - `pm2 list`

       - `pm2 logs zombs-proxy --lines 50`
         **Should show listening and session saver started**


   10. Go onto google or chrome whatever then go to the vps's site

       - `http://(YOUR-VPS-IP)`


   11. Congrats you now have a vps site you can send sessions on    
      





































   
                                      


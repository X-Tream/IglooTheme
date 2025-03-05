#Create a new Ubuntu server 24.04

#Install dotnet sdk
sudo apt update && sudo apt upgrade -y
sudo apt install -y dotnet-sdk-8.0

#Install nginx
sudo apt install nginx

#Configure nginx
#Replace /etc/nginx/sites-available/default with the following:
#(Change the port if required)
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        server_name _;

    		location / {
    			proxy_pass http://localhost:7320; #Change this if required
    			proxy_http_version 1.1;
    			proxy_set_header Upgrade $http_upgrade;
    			proxy_set_header Connection keep-alive;
    			proxy_set_header Host $host;
    			proxy_cache_bypass $http_upgrade;
    			proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    			proxy_set_header X-Forwarded-Proto $scheme;
    		}
}

#Copy the project files to /var/www/IglooTheme etc. using ftp

#Run dotnet project in /var/www/IglooTheme
dotnet run IglooTheme.csproj

#Open the website (IP of the server etc) in browser
http://95.216.145.71

#Chrome error
#ERR_EMPTY_RESPONSE

#backoffice works
http://95.216.145.71/umbraco

#backoffice username
teemu.heinonen@gmail.com

#backoffice password
by request

#In Windows 11 everything works as expected.

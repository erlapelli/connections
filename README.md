
#DevTinder 
-Create a Vite + React application 
-Remove unecessary code and create a Hello World app
-Install Tailwind css
-Install Daisy UI 
-Add NavBar component to App.jsx file
-Create  a NavBar.jsx seperate Component file
- Install react router dom 
- Create BrowserRouter > Routes > Route=/ Body > RouteChildren
- Create an Outlet in your Body Component 
- Create a footer 
- Create a Login Page 
- Install axios 
- CORS - install cors in backend => add middle ware to with configurations: origin, credentials:true  
Whenever you're making API call so pass axios {withCredentials:true}
-Install react-redux+ @reduxjs/toolkit=> Provider => createSlice => add reducer to store 
=> Login and see if your  data is coming properly in the store  
=> NavBar should as soon as user logs in 
=> Refactor our code to add constants file + create a component folder 
=> you should not be access other routes without login 
=> if token is not present, redirect user to login page 
=>Logout feature
=>Profile Page
-GEt the feed and add the feed in the store
-Edit Profile Feature 
-Show Toast Message on save profile 
- See all my connections 
- New page - See all my connections 
- New page - See all my Connection Requests 
- Feature - Accept/Reject Connection Request 
- Send/Ignore the user card from the feed




Body 
   NavBar 
   Route=/ => Feed 
   Route=/login => Login 
   Route=/connections => Connections 
   Router=/profile => Profile 





   # Deployement 

   -Signup on AWS 
   -Launch instance 
   -chmod 400 <secret>.pem 
   -ssh -i "devtinder-secret.pem" ubuntu@ec2-13-60-2-78.eu-north-1.compute.amazonaws.com
   - Install Node version 21.6.1 (Install the version that work fine in local that will work fine in aws machine without any bugs)
   -Git clone 
  -Frontend 
       - npm install -> dependencies install 
       - npm run build 
       - sudo apt update 
       - sudo apt install nginx 
       - sudo systemctl start nginx 
       - sudo systemctl enable nginx
       - Copy code from dist(build files) to /var/www/html/
       -sudo scp -r dist/* /var/www/html/
       -Enable port :80 of your instance 

 -Backend 
  -updated DB password 
  -allowed ec2 instance public IP on mongodb server
  -npm install pm2 -g 
  -pm2 start npm --name "decTinder-backend" -- start
  -pm2 start npm -- start 
  -pm2 logs 
  -pm2 list, pm2 flush <name> ,pm2 stop <name>,pm2 delete <name>
  -config nginx -/etc/nginx/sites-available/default
  - restart nginx - sudo systemctl restart nginx
  - Modify the BASEURL in frontend project to "/api"


Ngxinx config:

  Frontend = http://13.60.2.78/ 
  Backend = http://13.60.2.78:7777/ 

  Domain name = devtinder.com => 13.60.2.78

  Domain name = devtinder.com 
  Backend = devtinder.com:7777 => devtinder.com/api

 server_name 13.60.2.78 port

  nginx config :

     location /api/ {
        proxy_pass http://localhost:7777/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }


 # Adding a custom Domain name 

   - purchased domain name from godaddy 
   - signup on cloudflare & add a new domain name 
   - change the name servers on godaddy and point it to cloudflare 
   - wait for sometime till your nameservers are update ~ taken 15 minutes
   -DNS record: A devtinder.in in 43.204.96.49 
   -Enable SSL for wedsite 
   
   # Sending Emails via SES 
   
   - Create a IAM user 
   - Give Access to AmazonSESFullAccess 
   - Amazon SES: Create an Identity 
   - Verify your domain name 
   - verify an email address
   - Install AWS SDK - v3 
   - code Example : https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/ses#code-examples
   -setup SesClient 
   -Access Credentials should be created in IAm under securitycredentials Tab 
   -Add the credentials to the env file 
   - Write code for SESClient 
   - Write code for sending email address 
   - Make the email dynamic by passing more params to the run function 
   

# Scheduling cron jobs in NodeJs 
- Installing node-cron 
- Learning about cron expressions syntax - crontab.guru 
- Schedule a job 
- date-fns 
- Find all the unique Id who have got connection Request in previous day 
- Send Email 
- Explore queue mechanim to send bulk emails 
- Amazon SES Bulk Emails 
- Make sendEmail function dynamic 
-bee-quee & bull npm packages 



# Real Time using Websocket(Socket.io)

- Build the UI for a chat window on /chat/:targetUserId
- Setup socket.io in backend 
- npm i socket.io 



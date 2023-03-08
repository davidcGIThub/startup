# startup
Startup application for CS260. This readme describes the overview of the 
application as well as usage and development notes. See the introduction for setup.

1. Github Assignment

 - I already knew how to use github so I did not learn very much. However it is nice to use GitLens 
 to resolve merge conflicts rather than doing it manually

2. Startup Deliverable

    Elevator Pitch
        - Circles is the app that gets you connected in the community. Sick and tired of social media, but still
        want to know whats going on in the area? Circles is the best plan events, create groups, or just chat 
        with friends. You can also look up local deals in the area for interesting and fun things to do.

    App Features
    
        - This app allows you to create events, or groups, and invite your friends! You can also find events in your
        area. You can add friends and connect with new people in groups or events that you attended. The search page
        is key because it allows you to find events or groups by category

        - You can also create group chats
        
        - Stretch goal would be to expand the profile of each person so that they can find people with similar hobbies
        etc and connect directly with others.

3. Amazon Web Services EC2

    Elastic IP address: 3.134.54.227

    ssh -i developer_key.pem ubuntu@3.134.54.227  // ssh into server

    chmod 400 developer_key.pem    // this secures the key


    I though it was interesting that an IP address only gets changed when the server gets restarted. 
    
    The Caddyfile is the configuration file for your web service gateway. 
    
    The public_html directory contains all of the static files that your are serving up directly through Caddy when using it as a web service.  
    
    The services directory is the place where you are going to install all of your web services once you build them. 

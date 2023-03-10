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

4. Amazon Web Services - Route 53

    citycircles.net

    Route 53 is the AWS service that handles everything DNS (domain name system).

    You can look up info about the domain owner using whois [domain name].

    The NS records contains the names of the authoritative name servers that authorize you to place DNS records in this DNS server. Those same authoritative name servers are listed with the registrar that you leased your domain name from. That way the authoritative name server can verify that the DNS records and the DNS registration match and are authorized to represent the domain name when defining DNS records.

    The start of authority (SOA) record provides contact information about the owner of this domain name.
    
    
    
MIDTERM NOTES
 
Keys to learning how to be an exceptional programmer 
	1.Technology 
	2. Art 
	3. Social 
	4. Discover 

HISTORY OF THE WEB

	1. The formation of the internet that supports the communication of web applications 
	2. The creation of HTML and HTTP that made it possible to shared hyperlinked documents (Web 1.0). 
	3. The creation of CSS and JavaScript that enabled interactive web applications (Web 2.0). 
 
 PAIRED PROGRAMMING
 
 	Pair programming follows a very specific process where one member of the pair is the driver and the other is the 	navigator. The Navigator researches and outlines the overall design. The driver handles the keyboard and controls the tactical implementation details. After a reasonable milestone is achieved, or time period (~30 minutes) is exceeded, the driver and navigator switch. It is also important to celebrate milestones together. Cookies work great as motivational rewards.
 	
 
HOW DOES THE INTERNET WORK

Each server has an IP address. Clients are indirectly connected through the internet through ISP (internet service provider). Information is sent in packets, layers of packets are added and removed as there are sent and sent back. Domain names are converted to IP addresses by doing a lookup in the Domain Name System (DNS) 

 TCP/IP MODEL

	1. Application Layer  
	Functionality - (web (HTTP), mail (SMTP), files (FTP), remote shell (SSH), and chat (IRC) 

	2. Transport Layer 
	breaks the application layer's information into small chunks and sends the data 

	3. Internet layer 
	actual connection, This finds the device you want to talk to and keeps the connection alive 

	4.link layer 
	Physical connections and hardware 

DOMAIN NAMES
	TLD (Top Level Domain) - examples, .org, .net
	whois [domain name]
	
	DNS (Database records) - "A" record is a straight mapping from a domain name to IP address.
	 - A "CNAME" record maps one domain name to another domain name. This acts as a domain name alias.  
	 
	(TTL) time to live, setting for how long cache stores domain record (cache stores it for faster connection.
	
WEB SERVERS

	A computing device that is hosting a web service, that knows how to accept incoming internet connections and speak the HTTP application protocol. 
	Currently we build web services right into the web application. You can use "Go" web programming application to do that. 
	Web service gateways (reverse proxy) to map services to a port that is itself a simple web service that listens on the common HTTP port 443 
	Microservices = Web services that provide a single functional purpose are referred to as microservices. They are beneficial to because they can be managed independly from a larger system, also you can run several copies or instances of the microservice to be able to service several users at a time. 
	Severless functionality – where the server is removed from the architecture and you just write a function that speaks HTTP 
	
	
CADDYFILES
	The Caddyfile is the configuration file for your web service gateway. Caddy is a web service that listens for incoming HTTP requests.Caddy handles all of the creation and rotation of web certificates. This allows us to easily support HTTPS.  serves up all of your static HTML, CSS, and JavaScript files. All of your early application work will be hosted as static files. Caddy acts as a gateway for subdomain requests to your Simon and start up application services. For example, when a request is made to simon.yourdomain Caddy will proxy the request to the Simon application running with node.js as an internal web service. 
	
	The public_html directory contains all of the static files that your are serving up directly through Caddy when using it as a web service. A request for http://yourdomainname/index.html will look for a file named index.html in the public_html directory. 
	
	The services directory is the place where you are going to install all of your web services once you build them. 
	
	Route 53 is the AWS service that handles everything DNS (domain name system) 
	
 
 HTTPS & TLS
 
	Secure Hypertext Transport Protocol (HTTPS) - HTTP with a negotiated secure connection that happens before any data is exchanged. Having a secure connection means that all the data is encrypted using the TLS protocol. 
	The browser will compare the certificate domain name to the one represented in the URL and if they don't match, or the certificate is invalid or out of date, it will display a massive warning. 
 
	Web certificates are generated by a trusted 3rd party using public/private key encryption. The certificate issuer is responsible for verifying that the certificate owner actually owns the domain name represented by the certificate. Once you have a certificate for your domain name, you can serve the certificate from your web server and then the browser can validate the certificate by using the public keys of the certificate issuer. 
	
	The objective of Let’s Encrypt and the ACME protocol is to make it possible to set up an HTTPS server and have it automatically obtain a browser-trusted certificate, without any human intervention. 
	
	
HTML

HyperText Markup Language (HTML) provides the foundational content structure that all web applications build on. HTML was originally designed to be a publishing format for web documents, or pages. From that original definition web programmers have morphed the web page concept into a web application where a page now represents either a single page application (SPA) or a large group of hyperlinked pages that form a multi-page application (MPA)

HTML ELEMENTS & TAGS

HTML elements are represented with enclosing tags that may enclose other elements or text. For example, the paragraph element, and its associated tag (p), designate that the text is a structural paragraph of text. 

Tags are delimited with the less than (<) and greater than (>) symbols. A closing tag will also have a forward slash (/) before its name.

HTML ATRIBUTES

Attributes describe the specific details of the element. For example, the id attribute gives a unique ID to the element so that you can distinguish it from other elements. The class attribute is another common element attribute that designates the element as being classified into a named group of elements. Attributes are written inside the element tag with a name followed by an optional value. You can use either single quotes (') or double quotes (") to delimit attribute values.

<p id="hello" class="greeting">Hello world</p>

HYPERLINKS

hyperlinks take you from one page to another another with a simple click. A hyperlink in HTML is represented with an anchor (a) element that has an attribute containing the address of the hyperlink reference (href). A hyperlink to BYU's home page looks like this:

<a href="https://byu.edu">Go to the Y</a>

HTML EXAMPLE

<!DOCTYPE html>
<html lang="en">
  <body>
    <main>
      <h1>Hello world</h1>
      <p class="introduction">
        HTML welcomes you to the amazing world of
        <span class="topic">web programming</span>.
      </p>
      <p class="question">What will this mean to you?</p>
      <p class="assignment">Learn more <a href="instruction.html">here</a>.</p>
    </main>
  </body>
</html>

HTML COMMENTS

You can include comments in your HTML files by starting the comment with <!-- and ending it with -->. Any text withing a comment block will be completely ignored when the browser renders it.

INDEX.HTML

By default a web server will display the HTML file named index.html when a web browser, such as Google Chrome, makes a request without asking for a specific HTML file.

HTML STRUCTURE ELEMENTS

The two major purposes of HTML is to provide structure and content to your web application. Some of the common HTML structural elements include body, header, footer, main, section aside, p, table, ol/ul, div, and span


FORM ELEMENT

The main purpose of the form element is to submit the values of the inputs it contains. Before JavaScript was introduced the form container element was essential because it was the only way for the browser to send the input data to a web server as part of a request to process the input and generate a new web page displaying the result of the input. 

<form action="submission.html" method="post">
  <label for="ta">TextArea: </label>
  <textarea id="ta" name="ta-id">
Some text
  </textarea>
  <button type="submit">Submit</button>
</form>

HTML INPUTS

The input element represents many different input types. (form, fieldset, input, select, optgroup, option, textarea, label, output, meter). You set the type of input with the type attribute. There are several different types to choose from. This includes different flavors of textual, numeric, date, and color inputs. In order to create an input you specify the desired type attribute along with any other attribute associated with that specific input. Example

<label for="checkbox1">Check me</label> <input type="checkbox" name="varCheckbox" value="checkbox1" checked />

"INPUT" ELEMENT TYPES

	The input element represents many different input types. This includes different flavors of textual, numeric, date, and color inputs.
	(text, password, email, tel, url, number, checkbox, radio, range, date, datetime-local, month, week, color, file, submit)

INPUT ATTRIBUTES

name - This is submitted as the name of the input if used in a form
disable - Disables the ability for the user to interact with the input
value - The initial value of the input
required - Signifies that a value is required in order to be valid

VALIDATING INPUT

Several of the input elements have validation built into them. This means that they will not accept a value that is not for example, a number, a URL, outside of a range, or an email address. You can also specify the required attribute on an input element to mark it as requiring a value before it can be submitted. You should also have validation built into your JavaScript that checks input data to ensures everything is valid before it is submitted.

HTML MEDIA ELEMENTS

The HTML elements that represent media include img, audio, video, svg, and canvas. The img, audio, and video elements are all simple references to an external file, but svg and canvas both contain the code for render a visual image that can even be animated.

<img
  alt="mountain landscape"
  src="https://images.pexels.com/photos/164170/pexels-photo-164170.jpeg"
/>

<audio controls src="testAudio.mp3"></audio>

<video controls width="300" crossorigin="anonymous">
  <source
    src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"
  />
</video>

<svg
  viewBox="0 0 300 200"
  xmlns="http://www.w3.org/2000/svg"
  stroke="red"
  fill="red"
  style="border: 1px solid #000000"
>
  <circle cx="150" cy="100" r="50" />
</svg>

<canvas
  id="canvasDemo"
  width="300"
  height="200"
  style="border: 1px solid #000000"
></canvas>
<script>
  const ctx = document.getElementById('canvasDemo').getContext('2d');
  ctx.beginPath();
  ctx.arc(150, 100, 50, 0, 2 * Math.PI);
  ctx.fillStyle = 'red';
  ctx.strokeStyle = 'red';
  ctx.fill();
  ctx.stroke();
</script>

CSS


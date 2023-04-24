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
    
5. Simon Html

	Determining the content, inputs outputs, of a web page is all determined by the html code. The asesthetics have not been touched yet really. What is common for inputs and outputs is to have preceding label where for=" " identifies the ID of the input. The Simon pad was created by Using SVG graphics paired with an html table. The repeating headers and footers allow navigation between different parts of the webpage.

6. CSS Practice

/#   is used to select ID's 
" " blank space is used to select types 
.    Is used to select classes 

To center something, for example a body 

body{ 
height: 50%; 
width: 50%; 
overflow: auto; 
margin: auto; 
position: absolute; 
} 

To center contents of body 
 
div{ 
margin-left: auto; 
margin-right: auto; 
width: inherit; 
height: inherit 
} 

To center text 
p{ 
text-align: center; 
} 

~ general sibling 
+ adjacent sibling 
< child 

7. Flex Practice

to switch between flex directions you have to specify both 

@media (orientation: portrait)
{
  main{
    flex-direction: column;
  }
}

@media (orientation: landscape)
{
  main{
    flex-direction: row;
  }
}





    
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

Cascading Style Sheets (CSS) converts the structure and content of HTML into a vibrant, responsive, experience. The initial objective of CSS was to simply style the HTML based upon the desires of the user, developer, and browser. In modern web applications CSS styling focuses more on helping the developer create complex renderings of dynamic content that is responsive to the actions of the user and the device the application is rendered on. 

CSS RULES

. A rule is comprised of a selector that selects the elements to apply the rule to, and one or more declarations that represent the property to style with the given property value.

example :
p {
  font-family: sans-serif;
  font-size: 2em;
  color: navy;
  text-shadow: 3px 3px 1px #cccccc;
}

The selector p selects all paragraph elements in the HTML document. The four specified declarations then: 1) change the font to use a san-serif font, 2) increase the font size to be twice as big as the default font, 3) change the text color to be navy, and 4) create a gray shadow for the text. 

ASSOCIATING CSS WITH HTML

There are three ways that you can associate CSS with HTML. 

1. The first way is to use the style attribute of an HTML element and explicitly assign one or more declarations.

<p style="color:green">CSS</p>

2. next way to associate CSS is to use the HTML style element to define CSS rules within the HTML document.

<head>
  <style>
    p {
      color: green;
    }
  </style>
</head>
<body>
  <p>CSS</p>
</body>

3. use the HTML link element to create a hyperlink reference to an external file containing CSS rules.

<link rel="stylesheet" href="styles.css" />

----> style.css

p {
  color: green;
}

CASCADING STYLES

Elements inherit the rules applied to their parents. Any declaration property defined at a lower level will override the higher declaration.

<body>
  <p><span style="color:black">CSS</span></p>
</body>

body {
  color: red;
}
p {
  color: green;
}
span {
  color: blue;
}


THE BOX MODEL

CSS defines everything as boxes. When you apply styles, you are applying them to a region of the display that is a rectangular box. Within an element's box there are several internal boxes. The innermost box holds the element's content. This is where things like the text or image of an element is displayed. Next comes the padding. The padding will inherit things like the background color. After padding is the border, which has properties like color, thickness and line style. The final box is the margin. The margin is considered external to the actual styling of the box and therefore only represents whitespace.

CSS SELECTORS

how to select the elements that a CSS rule applies to. 

ELEMENT TYPE SELECTOR

element name selector. By selecting the body element we will cascade our declaration down to all the children of the body, which is the whole document.

body {
  font-family: sans-serif;
}

CSS COMBINATORS

Descendant - list of descendatns (body section)
Child - list of direct children (section > p)
General Sibling - a list of siblings (p ~ div)
Adjacent sibling - a list of adjacent sibling (p + div)


Next we want to change the color of the second level headings (h2), but we only want to do that within the sections for each department. To make that happen we can provide a descendant combinator that is defined with a space delimited list of values where each item in the list is a descendant of the previous item. So our selector would be all h2 elements that are descendants of section elements.

section h2 {
  color: #004400;
}

CSS CLASS SELECTOR

Any element can have zero or more classification applied to it. If we want to bold the summary paragraphs we would supply the class name summary prefixed with a period (.summary).

.summary {
  font-weight: bold;
}

You can also combine the element name and class selectors to select all paragraphs with a class of summary.

p.summary {
  font-weight: bold;
}

CSS ID SELECTOR

ID selectors reference the ID of an element. All IDs should be unique within an HTML document and so this select targets a specific element. To use the ID selector you prefix the ID with the hash symbol (#)

#physics {
  border-left: solid 1em purple;
}

CSS ATTRIBUTE SELECTOR

Attribute selectors allow you to select elements based upon their attributes. You use an attribute selector to select any element with a given attribute (a[href]). You can also specify a required value for an attribute (a[href="./fish.png"]) 

p[class='summary'] {
  color: red;
}

CSS PSEUDO SELECTOR

CSS also defines a significant list of pseudo selectors which select based on positional relationships, mouse interactions, hyperlink visitation states, and attributes. 

section:hover {
  border-left: solid 1em purple;
}

CSS DECLARATIONS

CSS rule declarations specify a property and value to assign when the rule selector matches one or more elements.

background-color - color
border - color width style
border-radius - unit
box-shadow - x-offset y-offset blu-radius color
columns - number (3)
column rule - color width style (solid thin black)
color - color (rgb)
cursor - type (grab)
display - type (none)
filter - filter-function (grayscale 30%)
float - direction (right)
flex
font - family size style (arial 1.2em bold)
grid
height - unit (.25em)
margin - unit (5px 5px 0 0)
max-[width/height] - unit (20%)
min-[width/height] - unit (10vh)
opacity - number (.9)
overflow - [visible/relative/absolute/sticky] (scroll)
position - [static/relative/absolute/sticky] (absolute)
padding - unit (1em 2em)
left - unit (10rem)
text-align [static/end/center/justify] (end)
top - unit (50px)
transform - transform-function (rotate(0.5turn))
width - unit (25vmin)
z-index - number (100)

CSS UNITS

You can use a variety of units when defining the size of a CSS property. For example, a the width of an element can be defined using absolute units such as the number of pixels (px) or inches (in). You can also use relative units such as a percentage of the parent element (50%), a percentage of a minimum viewport dimension (25vmin), or a multiplier of the size of the letter m (1.5rem) as defined by the root element.

p {
  width: 25%;
  height: 30vh;
}


px - number pixels
pt - points (1/72 of an inch)
in - inches
cm - centimeters
% - percentage of parent element
em - multiplier of the width of the letter m in the parents font
rem - multiplier of the width of the letter m in the root's font
ex - multiplier of the of the height of the element's font
vw - a percentage of the viewport's height
vmin - a percentage of the veiwports smaller dimension
vmax - a percentage of the viewports larger dimension

CSS COLOR

CSS defines multiple ways to describe color, ranging from representations familiar to programmers and ones familiar to layout designers and artists.

keyword - A set of predefined colors (e.g. white, cornflowerblue, darkslateblue)

RGB hex - Red, green, and blue as a hexadecimal number, with an optional alpha opacity #00FFAA22 or #0FA2

RGB function - Red, green, and blue as a percentage or number between 0 and 255, with an optional alpha opacity percentage - rbg(50%, 255, 128, 0.5)

HSL - Hue, saturation, and light, with an optional opacity percentage. Hue is the position on the 365 degree color wheel (red is 0 and 255). Saturation is how gray the color is, and light is how bright the color is. hsl(180, 30%, 90%, 0.5)


CSS ANIMATION

You create CSS animations using the animation properties and defining keyframes for what the element should look like a different times in the animation. Let's walk through an example.


p {
  text-align: center;
  font-size: 20vh;

  animation-name: demo;
  animation-duration: 3s;
}

@keyframes demo {
  from {
    font-size: 0vh;
  }

  95% {
    font-size: 21vh;
  }

  to {
    font-size: 20vh;
  }
}

RESPONSIVE DESIGN

The ability to reconfigure the interface so the application accommodates and takes advantage of the screen's size and orientation is called responsive design.

 Display -The CSS display property allows you to change how an HTML element is displayed by the browser. The common options for the display property include the following.
 	none - Don't display this element.
 	block - display this element with a width that fills its parent A
 	inline - display this element iwth a width that is only as bis as its content
 	flex - dislay this elemnts children in a flexible orientation
 	grid - dislay this element's children in a grid orientation
 	
CSS META TAG
 
 Meta tag in the head element of all your HTML pages tells the browser to not scale the page.

CSS FLOAT

The float css property moves an element to the left or right of its container element and allows inline elements to wrap around it. 

CSS MEDIA QUERIES

the @media selector. This selector dynamically detects the size and orientation of the device and applies CSS rules to represent the structure of the HTML in a way that accommodates the change.
 	
@media (orientation: portrait) {
  div {
    transform: rotate(270deg);
  }
}

You can also use media queries to make entire pieces of your application disappear, or move to a different location.

@media (orientation: portrait) {
  aside {
    display: none;
  }
}

CSS GRID

The grid display layout is useful when you want to display a group of child elements in a responsive grid. We start with a container element that has a bunch of child elements.

<div class="container">
  <div class="card"></div>
  <div class="card"></div>
  <div class="card"></div>
  <div class="card"></div>
  <div class="card"></div>
  <div class="card"></div>
  <div class="card"></div>
  <div class="card"></div>
  <div class="card"></div>
</div>

We turn this into a responsive grid by including a CSS display property with the value of grid on the container element.

.container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  grid-auto-rows: 300px;
  grid-gap: 1em;
}

CSS FLEX

The flex display layout is useful when you want to partition your application into areas that responsively move around as the window resizes or the orientation changes.

<body>
  <header>
    <h1>CSS flex &amp; media query</h1>
  </header>
  <main>
    <section>
      <h2>Controls</h2>
    </section>
    <section>
      <h2>Content</h2>
    </section>
  </main>
  <footer>
    <h2>Footer</h2>
  </footer>
</body>

body {
  display: flex;
  flex-direction: column;
  margin: 0;
  height: 100vh;
}

header - flex: 0 80px - Zero means it will not grow and 80px means it has a starting basis height of 80 pixels. This creates a fixed size box.

footer - flex: 0 30px - Like the header it will not grow and has a height of 30 pixels.

main - flex: 1 - One means it will get one fractional unit of growth, and since it is the only child with a non-zero growth value, it will get all the remaining space. Main also gets some additional properties because with want it to also be a flexbox container for the controls and content area. So we set its display to be flex and specify the flex-direction to be row so that the children are oriented side by side.


header {
  flex: 0 80px;
  background: hsl(223, 57%, 38%);
}

footer {
  flex: 0 30px;
  background: hsl(180, 10%, 10%);
}

main {
  flex: 1;
  display: flex;
  flex-direction: row;
}

Now we just need to add CSS to the control and content areas represented by the two child section elements. 

section:nth-child(1) {
  flex: 1;
  background-color: hsl(180, 10%, 80%);
}
section:nth-child(2) {
  flex: 3;
  background-color: white;
}

That completes our original design, but we also want to handle small screen sizes. 

@media (orientation: portrait) {
  main {
    flex-direction: column;
  }
}

@media (max-height: 700px) {
  header {
    display: none;
  }
  footer {
    display: none;
  }
}

DEBUGGGING CSS

Using the Google Chrome debugger you can access the developer tools by right click on the HTML page element that you want to debug and select the inspect optiA new rising contender in the CSS framework space is Tailwind CSS and its associated component library Tailwind UI.on.

CSS FRAMEWORKS

CSS frameworks provide functions and components that commonly appear in web applications.

Tailwind - A new rising contender in the CSS framework space is Tailwind CSS and its associated component library Tailwind UI. uses smaller definitions that are applied specifically to individual HTML elements.

Bootstrap - Most popular but now most websites look like bootstrap. You can integrate Bootstrap into your web applications simply by referencing the Bootstrap CSS files from their content delivery network (CDN).

// Bootstrap styled button
<button type="button" class="btn btn-primary">Bootstrap</button>

// Default browser styled button
<button type="button">Plain</button>


UX DESIGN

1. Simplicity - keep things focused on a single purpose
2. Consistency - use current trends so page is easy to navigate
3. Navigation Controls
	a) app controls - user settings, payment, and help controls
	b) device controls - device specific controls sucha as a back, next, and home
	c) breadcrumb - a path of the user's walk through the application
	d) common actions - direct links to the locations based on the current view
4. Application Map - has the views that will present to the user (like state machine)
5. Device Controls - make sure it works
6. Breadcrumb - Dashboard > Beatles > Abbey Road > Come Together
7. Common Actions - anticipate where a user would commonly want to go 
8. Color
9. Typography - use at most 3 fonts, use consistently, San Serif font for buttons, 
                navigation links, and body text. Serif fonts are used for paragraph 
                headings. Monospaced fonts are for coding examples or text than need 
                alignment.
10. Iconography - common icons users are familiar with
11. Text - (Page title, Titles, Text, Secondary Text, Input)
12. Limiting Line Length 
13. Internationalization
14. Space - draws attention to certain areas, and leads the users on a path
15. Interaction - engage the user, invests the user in the result of their efforts.
16. Images - Avoid using images that are only used as space fillers.
17. Animation - Animation can help make your application come alive, but it also helps 
     confirm choices, demonstrate progress, and focus attention.
18. Decision Fatigue - limit the number of choices given at any point in time.
19. Device Aware - be aware of device users using
20. Device Size and Orientation
21. Performance - as load times increase from one second to five seconds it causes 90% 
         of the users to bounce
22. Short Circuit - alternative if that functionality is not available.
23. Accessibility - users with different accessibility needs, including users with 
        visual, physical, and audible impairments. 
        a) visual - High contrast themes, color selection, screen readers
        b) Closed captions, textual alternatives, visual animation
        c) Physical - Keyboard navigation, element ordering
24. Legal -  applicable regulation and the possibility of legal action
25. HIPA - (HIPAA) stipulates the management of medical records.
26. FERPA -  (FERPA) defines how student data can be stored, shared, and accessed.
27. ADA - (ADA) seeks to prohibit discrimination against individuals with diverse 
      accessibility
28. GDPR - GDPR) impacts all applications that are used by members of the European Union.
29. Walls - If you can learn to recognize user experience walls then there is a good 
       change that you can remove them
30. Complexity - A primary cause of complexity is that software vendors uncritically 
       adopt almost any feature that users want.
31. Payment - user is able to invest significant effort and content to the application before payment is required.. the process for entering payment information needs to be as effortless as possible.
32. Application Failure - user will be slightly less annoyed if you can explain what went wrong, provide a possible remedy, or explain the expected duration of the failure.
33. Security - he security walls you present should be proportional to the value of the resource you are trying to secure. 
34. Legal


JAVASCRIPT INTRODUCTION

 JavaScript is a weakly typed language based upon concepts found in C, Java, and Scheme. Typically JavaScript is executed using an interpreter at runtime. This has the advantage of making JavaScript very portable 
 
Function
	function join(a, b) {
  	return a + ' ' + b;
	}
	
Comments
	// Line comment

	/*
	Block comment
	*/
	
Code delimiters
	While not technically required in most cases, it is considered good form to end JavaScript statements with a semicolon (;). Code blocks, and their resulting scope, are defined with curly braces ({ }).
	
Playgrounds
	a)Use an online sandbox like CodePen.
	b)Use your browser's debugger. open Chrome and press F12 the debugger will display
	
	
JAVASCRIPT CONSOLE
	The JavaScript console object provides interaction with the JavaScript runtime's debugger console. The console object provides functionality for outputting the value of text and objects, running timers, and counting iterations.
	
	LOG - The basic usage of the console object is to output a log message.
		
		console.log('hello');
		// OUTPUT: hello

	TIMERS - see how long code runs

		console.time('demo time');
		// ... some code that takes a long time.
		console.timeEnd('demo time');
		// OUTPUT: demo time: 9762.74 ms
	
	COUNT - To see how many times a block of code is called you can use the count function.
		console.count('a');
		// OUTPUT: a: 1
		console.count('a');
		// OUTPUT: a: 2
		console.count('b');
		// OUTPUT: b: 1

JAVASCRIPT TYPE & CONSTRUCT

	DECLARING VARIABLES
		let x = 1;
		const y = 2;
	
	TYPE
		Null - not assigned value
		Undefined - not defined
		Boolean - true, false
		Number - 64 bit number
		BigInt - num arbitrary mag
		String - textual sequence of characters
		Symbol - an unique value
	OBJECTS
		Object - A collection of properties represented by name value pairs {a:3, b:'fish'}
		Function - object that can be called 	function a() {}
		Date - calendar dates and times       new Date('1995-12-17')
		Array - an ordered sequence of any type    [3, 'fish']
		Map - collection of key value pairs    new Map()
		Json -  lightweight data-interchange format    {"a":3, "b":"fish"}
	TYPE CONVERSIONS
		strict equality "===" "!=="
	CONDITIONALS
		if (a === 1) {
		  //...
		} else if (b === 2) {
		  //...
		} else {
		  //...
		  
		  
		Ternary operator
		a === 1 ? console.log(1) : console.log('not 1');
		
		complex predicates
		if (true && (!false || true)) {
		  //...
		}
	LOOPS
		for (let i = 0; i < 2; i++) {
		  console.log(i);
		}
		// OUTPUT: 0 1
		
		
		let i = 0;
		do {
		  console.log(i);
		  i++;
		} while (i < 2);
		// OUTPUT: 0 1
		
		
		let i = 0;
		while (i < 2) {
		  console.log(i);
		  i++;
		}
		// OUTPUT: 0 1
		
		
		const obj = { a: 1, b: 'fish' };
		for (const name in obj) {
		  console.log(name);
		}
		// OUTPUT: a
		// OUTPUT: b
		
		
		const arr = ['a', 'b'];
		for (const name in arr) {
		  console.log(name);
		}
		// OUTPUT: 0
		// OUTPUT: 1
		
		
		const arr = ['a', 'b'];
		for (const val of arr) {
		  console.log(val);
		}
		// OUTPUT: 'a'
		// OUTPUT: 'b'
		
	BREAK AND CONTINUE
		
		let i = 0;
		while (true) {
		  console.log(i);
		  if (i === 0) {
		    i++;
		    continue;
		  } else {
		    break;
		  }
		}
		// OUTPUT: 0 1
		  
		 
FUNCTIONS
	In JavaScript functions are first class objects. That means that they can be assigned a name, passed as a parameter, returned as a result, and referenced from an object or array just like any other variable.
	
	function hello(who) {
	  return 'hello ' + who;
	}

	console.log(hello('world'));
	// OUTPUT: hello world
	
	ANONYMOUS FUNCTIONS
	
	// Function that takes a function as a parameter
	function doMath(operation, a, b) {
	  return operation(a, b);
	}

	// Anonymous function assigned to a variable
	const add = function (a, b) {
	  return a + b;
	};

	console.log(doMath(add, 5, 3));
	// OUTPUT: 8

	// Anonymous function assigned to a parameter
	console.log(
	  doMath(
	    function (a, b) {
	      return a - b;
	    },
	    5,
	    3
	  )
	);
	// OUTPUT: 2
	
	
	CREATING PASSING AND RETURNING FUNCTIONS
	
	// Anonymous declaration of the function that is later assigned to a variable
	const add = function (a, b) {
	  return a + b;
	};

	// Function that logs as a side effect of its execution
	function labeler(label, value) {
	  console.log(label + '=' + value);
	}

	// Function that takes a function as a parameter and then executes the function as a side effect
	function addAndLabel(labeler, label, adder, a, b) {
	  labeler(label, adder(a, b));
	}

	// Passing a function to a function
	addAndLabel(labeler, 'a+b', add, 1, 3);
	// OUTPUT: a+b=4

	// Function that returns a function
	function labelMaker(label) {
	  return function (value) {
	    console.log(label + '=' + value);
	  };
	}

	// Assign a function from the return value of the function
	const nameLabeler = labelMaker('name');

	// Calling the returned function
	nameLabeler('value');
	// OUTPUT: name=value
	
	
	INNER FUNCTIONS
	
	function labeler(value) {
	  function stringLabeler(value) {
	    console.log('string=' + value);
	  }
	  function numberLabeler(value) {
	    console.log('number=' + value);
	  }

	  if (typeof value == 'string') {
	    stringLabeler(value);
	  } else if (typeof value == 'number') {
	    numberLabeler(value);
	  }
	}

	labeler(5);
	// OUTPUT: number=5

	labeler('fish');
	// OUTPUT: string=fish
	
ARROW FUNCTION

	This is a function in arrow syntax that takes no parameters and always returns 3.
	
	() => 3;
	
	The following definitions are equal
	
	const a = [1, 2, 3, 4];

	// standard function syntax
	a.sort(function (v1, v2) {
	  return v1 - v2;
	});

	// arrow function syntax
	a.sort((v1, v2) => v1 - v2);
	
	RETURN VALUES
	The return keyword is optional if no curly braces are provided for the function and it contains a single expression. In that case the result of the expression is automatically returned. If curly braces are provided then the arrow function behaves just like a standard function.
	
	() => 3;
	// RETURNS: 3

	() => {
	  3;
	};
	// RETURNS: undefined

	() => {
	  return 3;
	};
	// RETURNS: 3
	
	THIS POINTER
	
	A closure allows a function to continue referencing its creation scope, even after it has passed out of that scope.
	
	function makeClosure(a) {
	  a = 'a2';
	  const b = 'b2';
	  return () => [a, b];
	}
	
	const a = 'a';
	const b = 'b';

	const closure = makeClosure(a);
	
	console.log(closure());
	// OUTPUT: ['a2', 'b2']

	console.log(a, b);
	// OUTPUT: 'a' 'b'
	
	Closures provide a valuable property when we do things like execute JavaScript within the scope of an HTML page, because it can remember the values of variables when the function was created instead of what they are when they are executed.
	
ARRAYS

	const a = [1, 2, 3];
	console.log(a[1]);
	// OUTPUT: 2

	console.log(a.length);
	// OUTPUT: 3
	
	push - add item end array 					a.push(4)
	pop - Remove an item from the end of the array		x = a.pop
	slice - return a sub-aray					a.slice(1,-1)
	sort - Run a function sort an array in place			a.sort((a,b) => b-a)
	values - Creates an iterator for use with a for of loop       for (i of a.values()) {...}
	find - Find the first item satisfied by a test function	a.find(i => i < 2)
	forEach - Run a function on each array item			a.forEach(console.log)
	reduce - Run a function to reduce each array item to a single item     a.reduce((a, c) => a + c)
	map - Run a function to map an array to a new array		a.map(i => i+i)
	filter  - Run a function to remove items			a.filter(i => i%2)
	every	Run a function to test if all items match		a.every(i => i < 3)
	some	Run a function to test if any items match	a.some(i => 1 < 1)
	
	const a = [1, 2, 3];

	console.log(a.map((i) => i + i));
	// OUTPUT: [2,4,6]
	console.log(a.reduce((v1, v2) => v1 + v2));
	// OUTPUT: 6
	console.log(a.sort((v1, v2) => v2 - v1));
	// OUTPUT: [3,2,1]

	a.push(4);
	console.log(a.length);
	// OUTPUT: 4
	
OBJECTS AND CLASSES

	const obj = new Object();

	obj.c = [1, 2, 3];
	obj.hello = function () {
	  console.log('hello');
	};

	console.log(obj);
	// OUTPUT: {a: 3, b: 'fish', c: [1,2,3], hello: func}

	OBJECT LITERALS
	
	const obj = {
	  a: 3,
	  b: 'fish',
	};
	
	OBJECT FUNCTIONS
		entries	Returns an array of key value pairs
		keys	Returns an array of keys
		values	Returns an array of values
		const obj = {
		  a: 3,
		  b: 'fish',
		};

		console.log(Object.entries(obj));
		// OUTPUT: [['a', 3], ['b', 'fish']]
		console.log(Object.keys(obj));
		// OUTPUT: ['a', 'b']
		console.log(Object.values(obj));
		// OUTPUT: [3, 'fish']
	
			
	CONSTRUCTORS
	
		Any function that returns an object is considered a constructor and can be invoked with the new operator. Because objects can have any type of property value you can create methods on the object as part of its encapsulation.


		function Person(name) {
		  return {
		    name: name,
		    log: function () {
		      console.log('My name is ' + this.name);
		    },
		  };
		}
		
		const p = new Person('Eich');
		p.log();
		// OUTPUT: My name is Eich
		
	THIS POINTER
	
	context of an object it refers to a pointer to the object. 
	
	CLASSES
	
		You can use classes to define objects. Using a class clarifies the intent to create a reusable component rather than a one off object. Class declarations looks similar to declaring an object, but classes have an explicit constructor and assumed function declarations. 
		
		class Person {
		  constructor(name) {
		    this.name = name;
		  }

		  log() {
		    console.log('My name is ' + this.name);
		  }
		}

		const p = new Person('Eich');
		p.log();
		// OUTPUT: My name is Eich
		
		
		#name // makes this private
		
	INHERITANCE
		
		Classes can be extended by using the extends keyword to define inheritance. Parameters that need to be passed to the parent class are delivered using the super function. Any functions defined on the child that have the same name as the parent override the parent's implementation. A parent's function can be explicitly accessed using the super keyword.
		
		class Person {
		  constructor(name) {
		    this.name = name;
		  }

		  print() {
		    return 'My name is ' + this.name;
		  }
		}

		class Employee extends Person {
		  constructor(name, position) {
		    super(name);
		    this.position = position;
		  }

		  print() {
		    return super.print() + '. I am a ' + this.position;
		  }
		}

		const e = new Employee('Eich', 'programmer');
		console.log(e.print());
		// OUTPUT: My name is Eich. I am a programmer
		
		
JSON 
	JavaScript Object Notation (JSON). JSON provides a simple, and yet effective way, to share and store data. 
	DATA TYPES
		string	"crockford"
		number	42
		boolean	true
		array	[null,42,"crockford"]
		object	{"a":1,"b":"crockford"}
		null	null
		
	EXAMPLE
	
		{
		  "class": {
		    "title": "web programming",
		    "description": "Amazing"
		  },
		  "enrollment": ["Marco", "Jana", "فَاطِمَة"],
		  "start": "2025-02-01",
		  "end": null
	CONVERTING
		You can convert JSON to, and from, JavaScript using the JSON.parse and JSON.stringify functions.
}
		const obj = { a: 2, b: 'crockford', c: undefined };
		const json = JSON.stringify(obj);
		const objFromJson = JSON.parse(json);

		console.log(obj, json, objFromJson);

		// OUTPUT:
		// {a: 2, b: 'crockford', c: undefined}
		// {"a":2, "b":"crockford"}
		// {a: 2, b: 'crockford'}
		
REGULAR EXPRESSIONS
	you can think of them as textual pattern matchers. You use a regular expression to find text in a string so that you can replace it, or simply to know that it exists.
	
	const objRegex = new RegExp('ab*', 'i');
	const literalRegex = /ab*/i;
		
	const petRegex = /(dog)|(cat)|(bird)/gim;
	const text = 'Both cats and dogs are pets, but not rocks.';

	text.match(petRegex);
	// RETURNS: ['cat', 'dog']

	text.replace(petRegex, 'animal');
	// RETURNS: Both animals and animals are pets, but not rocks.

	petRegex.test(text);
	// RETURNS: true
	
REST
	But JavaScript provides the rest syntax to make this easier. Think of it as a parameter that contains the rest of the parameters. To turn the last parameter of any function into a rest parameter you prefix it with three periods. You can then you can call it with any number of parameters and they are all automatically combined into an array.
	
	function hasNumber(test, ...numbers) {
	  return numbers.some((i) => i === test);
	}

	hasNumber(2, 1, 2, 3);
	// RETURNS: true
	
SPREAD

	Spread does the opposite of rest. It take an object that is iterable (e.g. array or string) and expands it into a function's parameters. Consider the following.
	
	function person(firstName, lastName) {
	  return { first: firstName, last: lastName };
	}

	const p = person(...['Ryan', 'Dahl']);
	console.log(p);
	// OUTPUT: {first: 'Ryan', last: 'Dahl'}
	
DESTRUCTURING
	the process of pulling individual items out of an existing one, or removing structure. You can do this with either arrays or objects. This is helpful when you only care about a few items in the original structure.
	
	const a = [1, 2, 4, 5];

	// destructure the first two items from a, into the new variables b and c
	const [b, c] = a;

	console.log(b, c);
	// OUTPUT: 1, 2
	
EXCEPTIONS

	JavaStript supports exception handling using the try catch and throw syntax. An exception can be triggered whenever your code generates an exception using the throw keyword, or whenever an exception is generated by the JavaScript runtime. 
	try {
	  // normal execution code
	} catch (err) {
	  // exception handling code
	} finally {
	  // always called code
	}
	
	
	function connectDatabase() {
	  throw new Error('connection error');
	}

	try {
	  connectDatabase();
	  console.log('never executed');
	} catch (err) {
	  console.log(err);
	} finally {
	  console.log('always executed');
	}

	// OUTPUT: Error: connection error
	//         always executed

FALLBACKS

	The fallback pattern is commonly implemented using exception handling. To implement the fallback pattern you put the normal feature path in a try block and then provide a fallback implementation in the catch block. 
	
	function getScores() {
	  try {
	    const scores = scoringService.getScores();
	    // store the scores so that we can use them later if the network is not available
	    window.localStorage.setItem('scores', scores);
	    return scores;
	  } catch {
	    return window.localStorage.getItem('scores');
	  }
	}
	
SCOPE

	JavaScript has four different types of scope:

	Gobal - Visible to all code
	Module - Visible to all code running in a module
	Function - Visible within a function
	Block - Visible within a block of code delimited by curly braces
	
	VAR ignores block scope
	
	THIS represents a variable that points to an object that contains the context within the scope of the currently executing line of code. (Global, Function, Object)
	
	CLOSURE
	
	A closure is defined as a function and its surrounding state. That means whatever variables are accessible when a function is created are available inside of that function. This holds true even if you pass the function outside of the scope of its original creation.
	
	globalThis.x = 'global';

	const obj = {
	  x: 'object',
	  f: function () {
	    console.log(this.x);
	  },
	};

	obj.f();
	// OUTPUT: object
	
MODULES

	JavaScript modules allow for the partitioning and sharing of code. Because modules create a file based scope for the code they represent, you must explicitly export the objects that you want to be visible outside the module. For example, here is a simple module that exports a function that displays an alert. You can import the module's exported function into another module using the import keyword.
	
	export function alertDisplay(msg) {
	  alert(msg);
	}
	
	
	import { alertDisplay } from './alert.js';
	alertDisplay('called from main.js');
	
	INDEX.HTML
	
	<html>
	  <body>
	    <script type="module">
	      import { alertDisplay } from './alert.js';
	      window.btnClick = alertDisplay;
	    </script>
	    <button onclick="btnClick('called from index.html')">Press me</button>
	  </body>
	</html>
	
DOM

	The Document Object Model (DOM) is an object representation of the HTML elements that the browser uses to render the display. The browser also exposes the DOM to external code so that you can write programs that dynamically manipulate the HTML.
	
	Every element in an HTML document implements the DOM Element interface, which is derived from the DOM Node interface. The DOM Element Interface provides the means for iterating child elements, accessing the parent element, and manipulating the element's attributes. From your JavaScript code, you can start with the document variable and walk through the every element in the tree.
	
	The DOM supports the ability insert, modify, or delete the elements in the DOM. To create a new element you first create the element on the DOM document. You then insert the new element into the DOM tree by appending it to an existing element in the tree.
	
	The DOM also allows you to inject entire blocks of HTML into an element. The following code finds the first div element in the DOM and replaces all the HTML it contains.
	
	All DOM elements support the ability to attach a function that gets called when an event occurs on the element. These functions are called event listeners. Here is an example of an event listener that gets called when an element gets clicked
	
PROMISES

	JavaScript executes as a single threaded application. That means there is only ever one piece of code executing at the same time. However, the fact that it does not execute concurrently does not mean that it does not execute in parallel. You can asynchronously execute code with the use of a JavaScript Promise. Because the execution is asynchronous the promise object can be in one of three states at any given point in time.

	pending - Currently running asynchronously
	fulfilled - Completed successfully
	rejected - Failed to complete\

	const delay = (msg, wait) => {
	  setTimeout(() => {
	    console.log(msg, wait);
	  }, 1000 * wait);
	};

	new Promise((resolve, reject) => {
	  // Code executing in the promise
	  for (let i = 0; i < 3; i++) {
	    delay('In promise', i);
	  }
	});

	// Code executing after the promise
	for (let i = 0; i < 3; i++) {
	  delay('After promise', i);
	}

	// OUTPUT:
	//   In promise 0
	//   After promise 0
	//   In promise 1
	//   After promise 1
	//   In promise 2
	//   After promise 2
	
ASYNC - AWAIT

	JavaScript Promise objects are great for asynchronous execution, but as developers began build large systems with promises they started wanting a more concise representation. This was provided with the introduction of the async/await syntax. The await keyword wraps the execution of a promise and removed the need to chain functions. The await expression will block until the promise state moves to fulfilled, or throws an exception if the state moves to rejected. For example, if we have a function that returns a coin toss promise.
	
		const coinToss = () => {
		  return new Promise((resolve, reject) => {
		    setTimeout(() => {
		      if (Math.random() > 0.1) {
			resolve(Math.random() > 0.5 ? 'heads' : 'tails');
		      } else {
			reject('fell off table');
		      }
		    }, 1000);
		  });
};

	ASYNC
	One important restriction for working with await is that you cannot call await unless it is called at the top level of the JavaScript, or is in a function that is defined with the async keyword. Applying the async keyword transforms the function so that it returns a promise that will resolve to the value that was previously returned by the function. Basically this turns any function into an asynchronous function, so that it can in turn make asynchronous requests.
	
	AWAIT
	
	the async keyword declares that a function returns a promise. The await keyword wraps a call to the async function, blocks execution until the promise has resolved, and then returns the result of the promise.

We can demonstrate await in action with the cow promise from above. If we log the output from invoking cow then we see that the return value is a promise. However, if we prefix the call to the function with the await keyword, execution will stop until the promise has resolved, at which point the result of the promise is returned instead of the actual promise object.

	TOGETHER
	
	You can see the benefit for async/await clearly by considering a case where multiple promises are required. For example, when calling the fetch web API on an endpoint that returns JSON, you would need to resolve two promises. One for the network call, and one for converting the result to JSON. A promise implementation would look like the following.

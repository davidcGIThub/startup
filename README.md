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
	
	



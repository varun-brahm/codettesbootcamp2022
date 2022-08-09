<link rel="shortcut icon" type="image/png" href="favicon.png">

<h1>Varun Brahmadin's Documentation</h1>

<a href="#CB1">Chapter 1.</a> 

<a href="#CB2">Chapter 2.</a> 

<a href="#CB3">Chapter 3.</a> 

<a href="#CB4">Chapter 4.</a> 

<a href="#CB5">Chapter 5.</a> 

<a href="#CB6">Chapter 6.</a> 

<a href="#CB7">Chapter 7.</a> 

<a href="#CB8">Chapter 8.</a> 

<a href="#CB9">Chapter 9.</a> 

<a href="#CB10">Chapter 10.</a> 

<a href="#CB11">Chapter 11.</a> 

<a href="#CB12">Chapter 12.</a> 

<a href="#CB13">Chapter 13.</a> 


<a id="CB10">
<br><h1> chapter 10. Interface & Application Programming </h1></a>
<br>Objectives
<br>Wk 1
<br>[x] Setup Dev Environment for ESP32 S2
<br>[x] Setup NodeJS Dev Environment on your PC
<br>[ ] Explain the HackOmation quadrant in relation to your final project.
<br>[x] Build UI mockups for your FInal Project and HTML Layout
<br>Wk 2
<br>[x] Build HTML5 Chat app
<br> Draw mockup / layout
<br> frame and add id’s to ```<div>```’s
<br> Style the page and 
<br> wire up the JS code and understand
<br>Wk 3
<br>[ ] Build Chat app back-end NodeJS
<br>Build NodeJS server side to: 
<br> host your ChatApp (Express static HTML)
<br> Build / test API endpoints (for: users & messages)
<br>Wk 4
<br>[ ] Setup MongoDB datastore & connect via NodeJS
<br> Setup MongoDB datastore + mongoose ODM (Object-Document-Manager)
<br> Store and recall message data using an API (ex. request top 100 msg)
<br> Wire up MongoDB to API endpoints
<br>Update app-flow to use back-end for Users and “old” messages
<br>Wk 5
<br>[ ] Create data-bound widgets to display sensor data
<br> On ESP32 add MQTT client + ArduinoJSON
<br> Send Sensor data to MQTT server (as a JSON object)
<br> Create a DataCard, a Gauge and a time Chart widget on Dashboard (use chat app)
<br> Strategy on DataBinding and Widget updating (Last updated)
<br>User Login/Pw (state persistence)
<br>[x] Add Screenshots and description of the process of creating your board.
<br>[x] Describe the design & programming steps
<br>[x] Screenshots or video of your Prototype/app working
<br>[x] Describe any errors or problems with the process and how you fixed them. 
<br>[x] Include all the files you created for download.

10.1 Build HTML5 Chat app
---------------------------

<br>So our objective was to build a chat app with a mqtt server. We first started by installing mqtt lens so we can connect to a public server. After that we made our mockups(pic 1) and put the drawings into code. After that we connected to the mqtt server with javascript, to make sure we had a connection. After that it was just adding functions and building a front end for it. After I connected to the mqtt server(pic2), I could send and receive messages(pic3).  I worked on the front end and styled it with css(pic 4)


      
<br>Here we have my mockup  
<br><img src="images/image4.jpg" alt="Draft" style="width:800px;height:600px;">

<br>After that we build our app with just the tags and the basic setup and connected it with a basic script. 

<br>After we had connected to the mqtt server, It was just a matter of styling and building extra features, 
<br>In the first picture, i have already connect to the mqtt server, but i couldnt send messages. Was a coding error, but it got fixed pretty soon
<br><img src="images/image2.jpg" alt="Draft" style="width:800px;height:600px;">

<br>In the second picture, I can now write from the chat app and also read, So i had the basics covered
<br><img src="images/image1.jpg" alt="Draft" style="width:800px;height:600px;">



<br>In the last pic i just styled it with css
<br><img src="images/image3.jpg" alt="Draft" style="width:800px;height:600px;">

<br>Problems  
<ul>
<li>mqtt server</li>
<li>Lessons learned</li>
<li>I got my web dev skills back, i forgot most of the tags tbh, but yeah refreshed it, Owh i learned javascript i never really went into that, and i also got working with mqtt servers and how those work</li>
</ul>
<br>Files & Downloads

<li>Chatapp.html</li>
<li>Style.css</li>
<li>app.js</li>

<br>Code:

```
<!DOCTYPE html>
<html lang="en">
<head>


<script src="https://cdnjs.cloudflare.com/ajax/libs/paho-mqtt/1.0.1/mqttws31.js" type="text/javascript"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/mqtt/4.3.7/mqtt.min.js" type="text/javascript"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">


<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.0.0/dist/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">



<title>Chatt app</title>
<!--<link rel="icon" type="image/x-icon" href="logo.png"> -->
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">


<style>

* {
  box-sizing: border-box;
}

body {
  font-family: Arial, Helvetica, sans-serif;
}

/* Style the header */
header {
  background-color: #d3d3d3;
  padding: 30px;
  text-align: center;
  font-size: 35px;
  color: white;
}

/* Create two columns/boxes that floats next to each other */
aside {
  float: left;
  width: 15%;
  height: 326px; /* only for demonstration, should be removed */
  background: #ccc;
  padding: 20px;
}

/* Style the list inside the menu */
nav ul {
  list-style-type: none;
  padding: 0;
}

article {
  float: left;
  padding: 20px;
  width: 85%;
  background-color:#524f4f;
  overflow:auto;

  height: 326px; /* only for demonstration, should be removed */
}

/* Clear floats after the columns */
section::after {
  content: "";
  display: table;
  clear: both;

}

/* Style the footer */
footer {
  background-color: #777;
  padding: 10px;
  text-align: center;
  color: white;
}

/* Responsive layout - makes the two columns/boxes stack on top of each other instead of next to each other, on small screens */
@media (max-width: 600px) {
  nav, article {
    width: 100%;
    height: auto;
  }
}


#cbox{

 align: bottom;

}

.cinput, select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}


#submit {
  width: 100%;
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

#submit:hover {
  background-color: #45a049;
}


.navbar {
  width: 100%;
  background-color: #555;
  overflow: auto;
}

.navbar a {
  float: left;
  padding: 12px;
  color: white;
  text-decoration: none;
  font-size: 17px;
}

.navbar a:hover {
  background-color: #000;
}

.active {
  background-color: #04AA6D;
}

@media screen and (max-width: 500px) {
  .navbar a {
    float: none;
    display: block;
  }
}


h5{

background-color: black;
color: white;
padding: 6px 7px 8px 9px;
box-sizing: border-box;
  
}

.list-group list-group-flush{
background-color:black;


}


.pp {
  border: none;
  color: black;
  #padding: 8px 16px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 14px;
  margin: 0px 4px;
  cursor: pointer;
  float: left;
}

.con {
  border: none;
  color: black;
  #padding: 8px 16px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 14px;
  margin: 0px 4px;
  cursor: pointer;
  float: left;
}



</style>

</head>
<body>

<div class="navbar">
  <a class="active" href="#"><i class="fa fa-fw fa-home"></i> Home</a> 
  <a href="#"><i class="fa fa-fw fa-search" ></i> Search</a> 
  <a href="#"><i class="fa fa-fw fa-envelope"></i> Contact</a> 
  <a href="#"><i class="fa fa-fw fa-user"></i> Login</a>
  <input id ="username" class="usernam" type="text" placeholder="Type a message"></input>
</div>


<header>
  <h3>Chatapp</h3>
  <button  class="pp" onclick="connect(sendPing())">Ping </button>
  <button class="pp" onclick="sendPong()">Pong </button>
  <button class="con" onclick="connect()">connect </button>
</header>

<section>
 <aside>
 <h1>Users</h1>
 <div id="userlist"></div> 

  </aside>

   <article id="chatlog">
    <h1>Chats</h1>
  </article>

</section>


<footer >
  <input id ="chatInput" class="cinput" type="text" placeholder="Type a message" onkeydown="sendMsg(this)"></input><br>
  
<button id="submit"  onclick="sendMessageButton(getElementById('chatInput').value); getElementById('chatInput').value='';">Submit </button>

</footer>
<script>



	// Chat app MQTT settings
	var mqttServer = "ws://broker.hivemq.com:8000/mqtt";
	var mqttTopic= "codettes2022";
	var userName = document.getElementById("username").value ||"Varun";
	const clientId = 'cb22_' + Math.random().toString(16).substr(2, 8)
	var userList = [];

//var client ;

	// Chat app MQTT settings
	//var mqttServer = "ws://broker.hivemq.com:8000/mqtt";
	//var mqttTopic= "codettes2022";
	//var userName = document.getElementById("username").value ||"Varun";
	//const clientId = 'cb22_' + Math.random().toString(16).substr(2, 8)
	//var userList = [];

	const opts = {
	  keepalive: 30,
	  clientId: clientId,
	  protocolId: 'MQTT',
	  protocolVersion: 4,
	  clean: true,
	  reconnectPeriod: 1000,
	  connectTimeout: 30 * 1000,
	  will: {
	    topic: 'WillMsg',
	    payload: 'Connection Closed abnormally..!',
	    qos: 0,
	    retain: false
	  },
	  rejectUnauthorized: false
	}
 
	console.log('connecting mqtt client')
	var client = mqtt.connect(mqttServer, opts);
  

	client.on('error', function (err) {
	  console.log(err)
	  client.end()
	})

	client.on('connect', function () {
	  // Once a connection has been made, make a subscription and send a message.
	  console.log('client connected:' + clientId)
	  client.subscribe(mqttTopic, { qos: 0 })
	  client.publish(mqttTopic, userName + " signed on!", { qos: 0, retain: false })
	  sendPong();
	})


	client.on('message', function (topic, message, packet) {
	  msg = message.toString(); // library delivers  buffer so convert to strig first
	  console.log("onMessageArrived: "+ msg);
	  // if it has JSON payload do NOT add to chat
	  try{
	  	msgObj = JSON.parse(message.toString()); // t is JSON so handle it how u want
	  	// if message has Pin of Pong in it send it to the PingPongHandler
	  	if (Object.keys(msgObj)[0] == "ping"){sendPong();};
	  	if (Object.keys(msgObj)[0] == "pong"){handlePong(msgObj.pong);}; // pong value is an object!!
	  	// other handlers for control messages below

	  }catch {
	  	document.getElementById("chatlog").innerHTML += "<br> >> " + msg;	
	  }
	})

	client.on('close', function () {
	  console.log(clientId + ' disconnected')
	})		
  
	  
	function sendMessageButton(msgtext){
	  	if (msgtext!=''){
			var name={varun};
			client.publish(mqttTopic, userName + " says: " + msgtext+ JSON.stringify(name));	  	
		} 
	}

	// OR listen to the Enter event on n input box
	function sendMsg(ele) {
	    if(event.key === 'Enter') {
			client.publish(mqttTopic, userName + " says: " + ele.value);
	        //alert(ele.value); 
	        ele.value = ""; // reset the input after entering       
	    }
	}

	// --- To manage userlist implement a PING and PONG system ---
	// Ping will request an "alive sign" from all or any user
	// Pong function will respond to ping
	// handlePong pongs in the UI
	// Ping will be scheduled to run regularly as a KeepAlive signal

	function sendPing(usr='*'){
		// ping sends out a message to all (*) or any specific user to respond if ur there
		var pingObj={ping:usr};
		client.publish(mqttTopic, JSON.stringify(pingObj));
	}

	function sendPong(){
		// sends clientID and UserName in a JSON object (and whatever u need more)
		var pongObj={pong :{userName : userName, clientId:clientId}};
		client.publish(mqttTopic, JSON.stringify(pongObj));
		console.log(JSON.stringify(pongObj));
	} 

	// function that manages the UserList and other UI stuff related to PingPong
	function handlePong(pongObj){
		// Update Userlist with Pongs
		const index = userList.findIndex(object => {
		  return object.userName === pongObj.userName;
		});

		//console.log("index:" + index);
		if(index>=0){
			console.log("User exists");
			userList[index] = pongObj;
		} else{
	    	console.log("New User " + pongObj.userName);
	    	userList.push(pongObj); 				
		}
		//console.log(userList);
		redrawUserList();
	}

	function redrawUserList(){
		// Generate the userlist HTML
		var ulist="<ul>";
		userList.forEach(function (item) {
		    //var x = arrayItem.prop1 + 2;
		    ulist+= "<li>"+ item.userName + " <a href='#" + mqttTopic + "/" + item.clientId +"'><i class='fa fa-fw fa-phone'></i></a></li>"
		});
		ulist+="</ul>";
		//console.log(ulist);
		document.getElementById("userlist").innerHTML= "<br> >> " + ulist;
	}
	// to keep connection alive
	//setInterval(sendPong, 10000); // keeps ponging every 10 secs
	
</script>

</body>
</html>
```
 <br> <br>
 <a id="CB7">
<h1> Chapter 7: 3D Printing </h1>


3D Printing is putting layers of a material(filament) on top of each other. The material we use is pla or abs.So we also need to configure our cura for the specific 3d printer.  We are gonna use the Anycubic Predator

Filament types we can use: PLA, ABS 

PLA and ABS are both thermoplastics. PLA is stronger and stiffer than ABS, but poor heat-resistance properties means PLA is mostly a hobbyist material. ABS is weaker and less rigid, but also tougher and lighter, making it a better plastic for prototyping applications.

7.1 Cura
------------

First we need to install Cura version 5.0.0:

![](3d_image/image3.png)

 And just click through it

Add the Printer
---------------

Go to Settings - Printer - Add Printer

![](3d_image/image2.png)

Add a non-networked printer- Anycubic - Anycubic Predator

![](3d_image/image13.png)

Put Parameters
--------------

These parameters are for PLA on the Anycubic predator

Settings changed:

 Walls:  Wall thickness: 1.21

Top/Bottom: Top/Bottom Thickness 1.2

![](3d_image/image1.png)

Material:

Printing Temperature: 195

Build Plate Temperature: 60

Travel:

Enable Retraction: check

![](3d_image/image6.png)

![](3d_image/image5.png)

These are the parameters. Now we need to adjust them.

7.2 STL
---

I open tinkercad then 3d design and i wrote my name

![](3d_image/image12.png)

Then we go to export - stl

![](3d_image/image9.png)

And save the file as an stl

7.3 G-Code
------

G-Code is the language that the printer understands,  it's basically just coordinates for the printer nozzle, so it knows where to and what to do, with some more info

![](3d_image/image8.png)

Here we see the time, the amount of filament used, the min and max in all the axes and some more info after that we see the coordinates in the different axes

Okay next step is stl to gcode

We can get the stl from tinkercad, when we design and we have to convert it to gcode for the printer

Okay First we have to load an stl file.  WE go to File->Open File(s)                   ![](3d_image/image7.png)                     Now that our file is open. We have to scale our print to 104%

![](3d_image/image10.png)

And then lay it flat.

![](3d_image/image4.png)

And then slice it. Now We have the amount of time it's gonna take and the amount of grams of the filament.
<img src="3d_image/image11.png" alt="Draft" style="width:800px;height:600px;">
![](3d_image/image11.png)

And now we have to save it as G-code. We click on Save to Disk and then enter the name

Now we can put it on the sd-card and print it. That's for next time

7.4 Printing
---------------------------

 <br> <br>
<a id="CB3">
Chapter 3\. Business Model Canvas, Pitch & Poster</a>
=========================================


3.1 Objectives
--------------

Wk 1

-   [ ] Setup your BMC for final project

-   [ ] Setup Pitch Deck

-   [ ] Create project poster

-   [ ] Add Screenshots and description of the process of creation. 

-   [ ] Describe the design & programming steps

-   [ ] Screenshots or video of your Prototype/app working

-   [ ] Describe any errors or problems with the process and how you fixed them. 

-   [ ] Include all the files you created for download.

3.2 Setup project BMC
---------------------

### What is BMC ?

 The Business Model Canvas is a template used for developing newand documenting existing ones. It offers a visual chart with elements describing a firm's or product's , infrastructure, customers, and finances, assisting businesses to align their activities by illustrating potential trade-offs.

Canvas were initially proposed in 2005 by Alexander Osterwalder

In other words its your whole business plan on 1 sheet of paper ![](https://lh6.googleusercontent.com/Nth3Mk9Zt2Twy4P50fsRYHeob6spNry7w64aKZOJhSOo9dD8E3XugH186Y37OlE5ixdOIeFU-Gaml9Pyylcwk8XfXyRZsZPLlM6qIhRyoaBS037Z4lANIbrLatNn_rfT0H5CCIzndLhLJJL7rhP3l3U)

Value proposition: What do u have to offer, What's so special about your product that the others dont have.

 Ex: Quick response, delivery till home or repairs till home

Customer Segments: Your target audience,  Who are the people u are selling to.

 Ex: Schools, Hotels but also people with covid for example 

Channels: How are u gonna reach your customers,  ads and where are you going to place those ads,  

Ex: Facebook 

Customer relationships: Make a platform so your customers always come back to you. 

Ex: custom coding

Key resources: The things you need to start your product.

 Ex: Tools,  Place to work,  if u have many workers a bus for example

Key activities: What are do things u need to do, before your product hits the market 

Ex: Make your own code or platform

Key partners: The less the better.  Your partners in the product 

Ex: Telesur

Cost structure: everything on the key side

Revenue stream: everything on the customer side

### My Progress 

My canvas: <https://next.canvanizer.com/canvas/iYxVgoqjYPIHP>

So now i am still playing with canvanizer, So i just put for value a submarine with a service and don't mind the customer segments

3.3 Setup project PitchDeck
---------------------------

3.4 Project poster
------------------

Please use HEADINGS and create some structure in your documentation

Files & Downloads
-----------------



Containing:








<a id="CB4">
Chapter 4: Freecad</a>
==================

4.1 Installing freecad and inkscape
-----------------------------------

![](https://lh5.googleusercontent.com/cOuF5VRFNvOoLVMVPDU2lb8zxVm92rGYwaMEW95ARKS93BzyM1HZam-xq-E5VBWPIVacJ3rH-DhDeHAp-FqH3n2jMpAUXYwESAdFix2u1zoWZN_p05UN4KxoAoVCVtaJsPhDSfcEmF-DYpdiZN9o5uk) Just run the freecad installer and click through it ![](https://lh6.googleusercontent.com/C5dlwU5_0Cy3Zq00ks8ldHPnMEC4AvMnogAXD-j1W1Em6UTeEE_BphivHQZoHHBHWkIasAY2aZQHw9wxscw_RNawGTC3XY_dTzjeHveDcgc7lxhRNYT780ri44ZvUNDuJ35aKpBGSp8z-E4D6P6h4i4)

Next run the inkscape installer and click through it

4.2 Creating a hole in Freecad 
-------------------------------

First we create a new object 

![](https://lh4.googleusercontent.com/24E7z4tM9MnIbcpRH-oh1jUfxdd2MMy6uc9J39XQlBfo9ISrc-9PX0qMUEJE8BUPo5QYdfzfeEsAz_LqtXEYXaS9lyqhq2nGqkN967wiWaOim-PmwB82rzVhrzOFAnsfYZD9OIqJJoJ0jwqNtPQ0_tE)

Create a new object

![](https://lh6.googleusercontent.com/VRfbuXTitlvgvafaP9dXNHiCdfVRbyScO3xaNTeDhyCa2iXGoPlCcpwDyYN024bfsYxhvhinl6amj0J1JYhxajOYlrj8gAet_cEGI8o-Rc-Iw0ptw8uTjR_mUut7RtAM56so_uu3B1ri6vrljc5i8Z4)

Instead of start-> Go to Part Design

![](https://lh3.googleusercontent.com/qKPjE2KKmgKFXg0KqNq0iRVg52KxAvK-LTNltQf8MpgyvwIDfNA7UnrUlxI7cHbs4S1IiNK-CclQZjG7oGpXcAnMMEfSTcEw-8cjHuCFaIkDsdXCN23DCA7g3ojFArzv_B9U3NX0FF-_ee-zdP7EhjQ)

Click on Create sketch

![](https://lh5.googleusercontent.com/ayF2bjEcbGJlNG1C9EEyYKh9LSqy4DGbx5bc-eAH1_IdjscI0YDKhNtTYSI4yWky9wBn-H8bwjLdMPGvo8TKyVxtHuIqK6mDt6cOQAk-bR0xcVvagczL0xZnFtvykNckc3Ya1vkqwsFAwY-VXjaU_pE)

Select XY_Plate and click on OK

![](https://lh5.googleusercontent.com/q5zfa608xfvxKXfZNE9Wa52UjbNd9wohtms7eDvcH6c2LuPJfK0EyddgsAQMIyPiZhgnnEwM8MLBVHCySJLh3wawSKF0mc8l2JpRjgoUbdczns2s_72Z6EizAu_HaJyOwsbS1D3cePRgtTsQNn-r9h8)

Go to Create Rectangle and click on it

![](https://lh6.googleusercontent.com/N2UYvlcDd0ceo4XDEP2Zh0JARm4W3qrt4EEIcYOZz2SOzSKAvTSX5bQC7ay6EvDpUmCK0iHBmM6E13HGe35rahWo8A4UXp0o70Jo4wZyEqq1zNVGF4UsMexEw17OMMS1cAWi9HgtV8FI9okGBBUqfb0)

And then Draw the rectangle

After that we need to adjust the length and width of the rectangle to 100mm

![](https://lh5.googleusercontent.com/3RLPM5J6V2xUgM__kqNXQmakbTWtFiv2H1GLO69EBezU8hiHiZmKT4lC2JgTsAlm0414wULDC85VYVLPkaozO_Hee95-4jSHLXAXo3Ig3BoPSjlVm0KYu9CKYc7UwOYrpRL9H8nhprtp1n3xKd8vxuQ)

We first go to "Contain horizontal distance"

And then click on the horizontal side

![](https://lh3.googleusercontent.com/7VSMGj5Z2R0msiT9S0CWRGnbdYnowCnl7c3_sB5n30je3E3hK-N5maE49MBp87zAEp_dc2tco0uKJsUhmttgSgTbck0o22DSQH6ZP-4vCyFyMcku5_lvBWEUslDtOU3L79OpC-EjC0-DlTuwtuatkQs)and then adjust it to 100

![](https://lh5.googleusercontent.com/Ez3Nt7odj1NDVEqxYF5OPLg1BScJUPkwZtqd7DK8XK6qQToQvcKlqzbg_5-wK3VkjLdb4Q73FnPUCoJLDoR903SJViTWSzPZmf5lX_pZRgTZYgs1ZXcNnc2R7lrOpeTBPneflLodOBtF2TtIXfnbsF8)then the vertical side

![](https://lh6.googleusercontent.com/sfqBjkf9gFWUVTBAftQhHDgcTVVlHw3P59RSCuoMxgslyy9iUcS7lM5qL3yviGQTPBkNtI74SuIh15XUm-IrHymUNPwy_6PsmdCXu3FI927o65Rn7bNTyfV2ytW8qR2O7vmZSwHdHyo6sXshVcBHHjI)

And then adjust the width to 100mm

--till here for creating a pocket---

![](https://lh3.googleusercontent.com/bYtd-FvnPeJ8ZS36TlDJ2BtEfB41bO8_xSRV4AkPPTOPTQqnTIe1g9v1RsTTKGvJrGpY67D0T-Q71o7xdFtW49UAeSXr8zmki4E8xkk7wFw7O07zFvtqQ3xs2HBlM335P6tt-10R2EHQmutzxcbaWVE)

After that choose the circle and draw one

After that click on close in the Task

![](https://lh3.googleusercontent.com/zKi50e7HpoSultLlojDxOm2g5lQW-uIHi4aI1aPA8aclEFTl59b_awSMIRS9PbGt3Glvpk8HId6VRnhioUg24Iy90omw_oEAWEj7Oa8ccwr4F6tkYWTVHKUhUU9V86ozLY9pMq7yUP5dvrbqPgLbFe0)

After u click on pad there will be a solid layer

![](https://lh5.googleusercontent.com/I3igdMHPjC1AMrDcww75DtZkWhtTRWby5cd_jFh_fYtn0zM2xsTAYhsBscCboaEDk28EdhA9q_AXe3sTr2p7Nmtfg6-3M3I2P4Wdoni-v-1yRpZdFehmryyCX9fLYTqrwArCMdgsfPMhNlsEqsbLLJQ)

Like this and now you also have a hole through it

4.3 Creating a pocket 
----------------------

You can follow the last documentation and its marked till where

You just click close and when back u can just click on pad 

![](https://lh6.googleusercontent.com/-xgLiVdK71JaZIN-dEH498u-87IjyrVEhtH_5GsGyyW7ZUrleVhkrl9XZHu3jHKKE-57Ee9G2n0aE5vRa23gbfRWCY10ljSn0j7OOWM5JYoVdZtertn4h-wgHr_7Pipe0wGKZEd00y3JX2Essgn5tl0)

U will have something like this, you can click ok after that you can click on create sketch again

![](https://lh5.googleusercontent.com/s8iq8akVo42s18b6LjiWBGbLxCjt5dqZywf4QOtkXZv-gqokiF3O9rdsLrFraHrlLPQzAXxc0dRUTcaAAdF979x7_fkn64lmbnaBbuzYQyAJqjyMTtiQNZnBVg2TbWgd7dkS0kD6EmFEtiBvhQKo46Y)

And you can select the XY_Plane

![](https://lh6.googleusercontent.com/QMnRBUfuzuHWiLG7ssnrMARPG85_XSmupPryPwxQXr6NKQbd8TebHWEYEZ-xZD8m5mosDftwTCsah5CnMzUtfN8MeM0b_FdneaJfuciHrPZcI2geoBQk_-ZmfjhZv-MNcwi-8z5xQO7MWX0b-8nBD-4)

After that you will see your solid design and you can draw a circle on it,  for more info on that check chapter 4.2

Note: The circle may come on the opposite side, but dont worry, just draw it and turn your design

![](https://lh4.googleusercontent.com/BguAdYfBntyIntdw2Nzottb4CbKZAyuSE1j07-WmqaAl7Q-37opt0mzEV1mFpetDWj_70Yt8SpBN3wEe-em2S56p1exnrWafz47riGWsIkbQezfhXHXopCqI7LbVOoB2mHPvhbYMTPYacGBXgJC3unw)

Here i already have the circle and i turned my design

You can click on close from here

![](https://lh4.googleusercontent.com/8qS7x1IT-eW79i3BjbztTWB6NVZ-l6UfZYZLPYbtPt8kXRgq_pW--d5_iy7lSaU6vw_Uz-zBEzVXvbRXTuCIXyoHMgxTuMsfbi0-tzAkSl0MiVRwDt66ybxUntT6OTL903wNZAAKuT-nmbuHv2ubO8U)

And now you can click on pocket and just close it from the task

![](https://lh5.googleusercontent.com/4d-vRqGPL6je_WH8Q87G65KKB-fh6pR45QDlZYP4_JbEmJm39wghoSVeKUNlK12foICtsprXuYwr1bbLqWfYJevZF7maH98kJrOg6yEYcg31QyMmK2TlCy55o9VBCZvkzduj2T-6ywM0JKwbk0XuD1Q)

The select the circle in the middle so it becomes a different color and click on pocket again

![](https://lh3.googleusercontent.com/m7d3eHVGu5TR6awH899oL_Dfffh2IvH_JqkkgJMvTykO269HM39cgj2rtz6P2H9WHRj-uyqReC9zn47nS0RNJmYM1FoqZ_v_D0CuE-dODcQTx2OYuTFi8XHouNPpy5ISHfWdWZQnMIwU4oiD02cWXT4)

Then you are left with something like this,  you can adjust the parameters if u want, its on the left side in the combo view in either Model or Task




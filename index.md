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

I presented my bmc and got feedback 

Value: 

1. Different models

2. Sensors

3. enviorment

4. Location estimate

5. Lidar

Customer relationships:
1. A webapp

2. Custom parts

Channels:

1. A website

2. Stores

Customer Segments:

1. Kids

2. Researchers

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

![](freecad/image18.png) Just run the freecad installer and click through it

 ![](freecad/image8.png)
Next run the inkscape installer and click through it

4.2 Creating a hole in Freecad 
-------------------------------

First we create a new object 


![](freecad/image5.png)
Create a new object

![](freecad/image2.png)
Instead of start-> Go to Part Design

![](freecad/image4.png)
Click on Create sketch

![](freecad/image15.png)
Select XY_Plate and click on OK

![](freecad/image17.png)
Go to Create Rectangle and click on it

![](freecad/image16.png)
And then Draw the rectangle

After that we need to adjust the length and width of the rectangle to 100mm

![](freecad/image11.png)
We first go to "Contain horizontal distance"

And then click on the horizontal side

![](freecad/image9.png) then adjust it to 100

![](freecad/image14.png) the vertical side
![](freecad/image9.png)
And then adjust the width to 100mm

--till here for creating a pocket---

![](freecad/image1.png)
After that choose the circle and draw one

After that click on close in the Task

![](freecad/image7.png)
After u click on pad there will be a solid layer

![](freecad/image19.png)
Like this and now you also have a hole through it

4.3 Creating a pocket 
----------------------

You can follow the last documentation and its marked till where

You just click close and when back u can just click on pad 

![](freecad/image21.png)
U will have something like this, you can click ok, Select the top and after that you can click on create sketch again

![](freecad/image20.png)
And you can select the XY_Plane

![](freecad/image13.png)
After that you will see your solid design and you can draw a circle on it,  for more info on that check chapter 4.2

Note: The circle may come on the opposite side, but dont worry, just draw it and turn your design

![](freecad/image12.png)
Here i already have the circle and i turned my design

You can click on close from here

![](freecad/image10.png)
And now you can click on pocket and just close it from the task

![](freecad/image3.png)
The select the circle in the middle so it becomes a different color and click on pocket again

![](freecad/image6.png)
Then you are left with something like this,  you can adjust the parameters if u want, its on the left side in the combo view in either Model or Task

4.4 Creating the holes
----------------------

First we created a object with 2 holes and 1 pocket

Parameters i used are: 100mm*100mm*10mm

Check the previous paragraphs for that

After we have that

![](https://lh5.googleusercontent.com/1bhYCJXNo_JXLV1S5ZqOXnZOaGy7kx0-BHVKGRfFeuybH3TB6vMo2QaSDzetk31F3mVqZw3Gi4c1oMIwmTxGDKsVjzKfT3lEsIYzyQkklJ4K5cSJe2Tl4OZ-NVYGwNEnw0W4hSefng0JZ3p7j0vmIFM)

U should have a object like this and then go and select Path

![](https://lh5.googleusercontent.com/4tXghW8Tsgtvar1Nikt6_odLERpXF_uog8_2gwi4WH5-vRMpGB4b3CkESjYtlN3Mn00TVyIS6RlLOr_hG2amnmWPWuky7vye5cwTIKyGEWgpRqp1QUV3odqqbK00UpzgVXoxw6kl2DsgKpIgkqutf20)

After you selected path go and click on job

![](https://lh4.googleusercontent.com/m32wow06pHBNH8wbptVBFc5-M6R_9BmrHAAHjMdR8JNzo95t-X0S0PIb_oJBxzufNIWKGNpNb6wGVJYro-NyZUzeLGd5_F12T67_FIVP6RwdU69608fplP_uX-moUSACrztU53CQrnF-sdD80rl-MZg)

I select body 1,  but i dont think its necessary and then just click on OK

![](https://lh5.googleusercontent.com/xcFNf_al_xGlm-o-i5mgO1HrQyE5BR9MLStQY4rQAgCpVUeSaQnAPSukPaiMoSNOl_SRydtQx09NYzwL9kBlIg7_lulLcsPlTXnux4fHFuzdgBQgP6uhcuIRlHL_AgFkH0npdSzdpXUCrPwe9FxHMig)

After that you will see that the purple bubble is on the bottom, you need to bring it to the top, So u have to precisely select the corner above it, in the picture you can see the corner is yellow(a small dot)

![](https://lh3.googleusercontent.com/8RNp57Mcppw-S14krmcOx6xeObxVhshrIPBgOo_x-pSV01l9KsHIi7gJ7DLVB5PFNW1lRYhK2LU2ADzVtgURfcUt9JTKLDgVgZxGEaZpoVP4R8pv30_EWp9UdHNrDXdi-e5kdivY4zqVFFYAVvt7AZo)

After you have selected the corner, go to Set Orgin and click on it and the click OK

![](https://lh3.googleusercontent.com/m5qenpwAD5Rhw5PzRbIZYpl5ic6GrQqjzndXeBKQmrQilCXXiYLs5k1P6YK899nmaHpBpzakF8nwwBxMvgwWrQtizLemcuLWW7sNFIrS3RkAJtuXy_Z7gEp8ctEsC5FWfxQcD84LVTwcdVFXvCeykM0)

After that go to ur body and press the space bar to hide it

![](https://lh3.googleusercontent.com/ShKV8cNqUfYtFD15e0axUxbq3Y-5-sCZdD93Dl2K2c6FqKs32zbufPDvTWCbsM7we0xuUEZpw76ItSiR5PYp8Thio2XsJUCyuoTkMFXSisLdYeGAaZb75xG73uQspEJzHvqbWE0p3i4KxzLTYyA-DOI)

After that go to Model Body and press the space bar to activate it

![](https://lh4.googleusercontent.com/lrPELkBUU2kGphSUh9de9kAZibRBtHA9O-YD8bBVjV7tyeiIZU8-wteIioK7yfdc8hnauwMpzCTKx_4NA9ab2qeES7upz8SKaeLKrjpN1w45E1IIl8AYrdkiba-IyeZlyXTwWrEOunb3YQBZtIVVyJc)

You will see something like this, after that click on ToolBit Dock

![](https://lh5.googleusercontent.com/nh1d1NIsOJlwpv9NElQbKA0oyRNBC7Hpxze8w25f7datIxBzUEhJHIxHBT7cifg-Glj3E4akahW7eM-t1bv2KXcImDKIUMKm4HN8ulNKpgeJ3U64GXTZ4EA5hfztexG7J43EyAA9dm2x5EmDKD-ZJC4)you will get a window on the right side, go to the top right of it to create a new tool bit

![](https://lh3.googleusercontent.com/q1wt1oNvRdbdqJfJiSTtAWJV7ZOQBUsjTnnPMIiPgjXAyT0Ybgzqla-yNRVgU7iLNzvStQUZ_PpfxjcISc1Mc2p8UCLkL1V6x-pdMwT3ad43xjniUM7Xgt3CsUasvkMNhwROZSKUnaZsYoMv_eNeiKE)

You will see something like this then, click on Create Toolbit

![](https://lh5.googleusercontent.com/oilR-0jhlLlHnVqZu2WA2_g0ef_7bgW40_Qhljvmy7CFyhudcRPT-r0S-1NbnHOEgS306apApq_HHDqPTmut6dfoDLE1KSRK2t0sbbTSat_oKoZsgTcMJ-TNt9yU9kcVFGgTmYVBMM8hrZLtv7W8yoI)

Select endmill and click on open

![](https://lh6.googleusercontent.com/USojdWPQrtaEdz-JyoBZJJyM-uuJfgh7vpiEoqB72ZuqrvTFB8FGMgLJviVUr0NppDL6k8FVHmXJ9A9Wi3grJBP48W4ybIzOwKAD0DRo0fil3bPIPo74F_y9UbePzw9_Xh4YWaYFRrYbQMYCY9Q7ZK0)

Here just name it something,  i would recommend the bitsize_endmill.fctb

![](https://lh4.googleusercontent.com/RFt2h52iY4jDJIAPxZAgkhfWGHsJNvAPG8aPe1OdH8WTSg8JvaZJGmadoW3Mz2ClS8Tsuri9td5qVwSoQ3vGBdKincFMjE5Q4QO3Rc1p-_rsvtmZiZqeqQAcu-_9QHBRdiks0Q1Ht8vLXp2HdxZiZwY)

Then you will have it added, i opened here an old one of mine by double clicking on it, so i can see the parameters. These are the parameters for the 3mm drill bit

![](https://lh6.googleusercontent.com/DAW_JjXJj3-s9n0mAYYUUH8W-pRZSOP86q4jmocxWHNYKlKwgEgB3tv6E3Dx4sOLbStJGlhZwdj1JHAk3l0Jaf7PnGSCkT8_rUs4iQIpSfvSO7yCPQ6L14LF_Q6_DNzFLuDJpSIGGBkRz-ATfHrp9to)

Then you will see it comes on the list on the right window, you can just select it and it will come on the left side, you can delete the default tool from there then

![](https://lh5.googleusercontent.com/PkXCgYS__SjF7MwBs2hP4u1vyHvGeCrFtx-qPbBz_UbsYbz3QzaAk1TeLUp4ytTjWt-Q6b4Y3I48dL1LRj_K4T4IwjZ2TFaTS1ZbPPsPU57SrStCmzsExhH-73op0_DhR3GT0RixLVNLBwW_BCJ-gVc)

Now go to pocket shape 

![](https://lh6.googleusercontent.com/6vkTQx0p5Vbs1OqNyy8kG8e39nA9MXmJj5CKaJOzWa6F8zqMou-H9Z06r6iqU1i3QycFX9vs-OtxsdGjWN1rxlvPUA9pKSLPgC6KyZjNUne47XKinFA-M_5i-BKl4GrzCdWvn0dbJgg11NeZKzYu7yw)

Here select cutmode: conventional 

![](https://lh3.googleusercontent.com/wbW9Y4Zo8l9YR_o8yvvtff4jyoVKMcfxF1KAVpqzO8VmKycfAlmd9QOborLFSmUb9kkLmaGkhqx3tD0z1Fjax1Rr6WJV6-0LrbfIvrJZjIaJtDEMLgfWshKX-Nbcvf7TfUdaa0FdXWv_rhAtP02d9rc)

and pattern: offset

![](https://lh4.googleusercontent.com/4KDXdWxZqhL0ttSHGTJJfaGPMRUn98SlbSnQfx87Bam6suvVXTPBuXE1fLV0u35kcQ5aPh0a4w9jly3qUh2RCByLbAeUvj1pZ6ztzc1wOau8odQq95fRxMzfHl5wmXDyo-sXPSMFPNGRDY0rK9IQf4M)

And check the box of use outline

![](https://lh3.googleusercontent.com/CUZh3i2kOr2QiBgfxUNmMUfHiWiH5UEf9Kfily-76i1to2Rt28iwchqVXsFikJh-0oh0cD4-GrSGzwuBt_3I4HtycK2sbL3G24ygIoU52CwJLQnNkV452kP7djL4QwsFxBijDkMGm2XUEUZxyO9iGxo)

Then go to Base geometry 

![](https://lh4.googleusercontent.com/jni7Wtsuw830RZRoGpOE0UXLy90TzLNRLz6-J0u7R0dGn60-rruubpRpxeayU3BBxwyRPlpnxonSyzFxW2DMNGSTblzHD1FIkE7CqkBUwOlpBhEoRMJo8DLAEGnNrMx7qAvIGb6zylpibICwBqM9Aqo)

And select the inner edge of the pocket, like this 

![](https://lh5.googleusercontent.com/N_FhehbtQ_ml_dtRMUMEN6VOQ8X96VVdXhsb9zSs9Iug_Cezhzdqh6KKn9knnbk3Wzwzrs0_cFsJosJMKTfExbsf8uDwdAqFrCtZvBWfc2I3DNcU_sneJkcPYTX084KfFqzjlDi7cWScyv9fguedhog)

Look now it is green, then click on add 

![](https://lh6.googleusercontent.com/mUoLzlU8902k1BLgUmNeukj5ANPwZmBDXo8mSNBfGNzTpNreBS5Ui067KcWh_bXtp0IK-xRPJGicRgNn3lz-UbZD3TWGQAT9ZzhZbLPstXQsZzDQLBziZaBlYKF5QBKuJ-4X-8BWxCIoXeuP79Kqa88)

And now its added

![](https://lh6.googleusercontent.com/bymYure5JKUfQ64DKtEQmdv70D6wSVSz45H1gsdzwBzhCN7oiMDVcJnSwM0gkKl1bLlTS0thgL5clNjleQzD185MDkgqiaLTIo3wVvLDr8u3nZxsC2BL-kQ_P4qtQDMSPKrR7kEHgY4wuUhpS1kjfsk)

Then go to depths. Here you also have to adjust the parameters. 

Start depth: 0.00mm(standard)

Final depth: -5.00mm(pocket depth)

Step down: 1.5mm(half of your bit diameter)

After that click on apply and OK

![](https://lh6.googleusercontent.com/ALrQToaepdKVrHoliEKEAu1V9GrqILJaa5TqfdHwXMIxNEW_ZIeafqai4u99TwuFlHMDnvjC_ktpWrvqtMMNrUYNHjPaoVBv_tN-NyEy3upTm2TfaSSQT0j_fOj-MugD9kOpkipHK7Fpcb1nfqTfi7k)

Then you can go to CAM Simulator

![](https://lh5.googleusercontent.com/WqZOG87lh3CQIad0zw4Y5zZtsPAWpAJ8UC1GNN4Bkpvxh_sPefHeFk9-FJiOAwnkKsc8hG7NssEj3ghqhqZDtKJ_hGk7yRWMMPAIdydK1Z1tesM3W86C4qUBTQaVFynvqwxw9wklSV5p0d0IT6KUeys)

And then just click on play 

![](https://lh6.googleusercontent.com/0Jg30LYbzsDtvyNikYdX0Xk2UYOP3frqMBYyJWQS7YwCatUd798z34ij-HwWflmrUKdEysV9qVmPCGaA1TQfzCT9wU3S_drkfsmsc5r-mKXNfiMVaVEJYFkdxlVWtZe5y7BVjUiIUInhxL2yP0Zhkok)and it will simulate making of the pocket for you

![](https://lh6.googleusercontent.com/xIh_1An4sZKXEDcmI3eoE4bjyKijGQ0sSQAoXK-oueLc3tdUL3AGgM_9CAX3fYH4j2InkD11OL9sVj4gO2HbXgyUznIA54KnRS2WX8V0xPNnVCS1L92SRzPa28eV-lLE0BgCciyqHCq5oxOp-jGaKaI)

Now the 2 holes, Click on Profile

![](https://lh6.googleusercontent.com/IGrPxw8D26SN8d6RvoRm6BnhpHV5RMue2ORumsqQqd9gMo8FqfJeRGPwNeEkOPP7LE6sA4JG9D66s10rBWaKd1TnGLuFFTTJSB97Kl-w8OlwzKG5roVx8GhnFFwh9uIhX0YiW1x-j4jLO5GIGwAtN1o)

Then select inside

![](https://lh6.googleusercontent.com/LEGjwVhE5AQarwwshiJgo_EVTyhVVHj4TrFYm_UIgCfzhJKfZaUguU7mYIE7TMp9Teoapq9yCOX64LIhHMoOFHLr1a8m9KoSmfH9b-cOBx5kzxoUVsrCH-ZPAM8NTRs-83Vv7w2FOHpMH44TM2v0q78)

Once here you also have to select the inner edge of the circle and click on Add

![](https://lh4.googleusercontent.com/-srmK2ldfy9cggrgJKMAXCMiQkZJmHp3Cb7ms6O59sxNZcrLmKNMwEoq44f7LTEjyCu0D1Bi-jX8vMKC0NtzA5Tgc8hBErX7aL6fjPSCDKZflPq-n6rOd-uud8C5MJ8PrTQS_B_MQw3CcjVFvFGMLEA)

Now the second one, click on the inner edge and click on Add

![](https://lh6.googleusercontent.com/rZb5CqglgxwG7dFZz-ckFNEYece_CSRzDac91OsgJyxXAZDOKm4_JYqNAFMHlF_1z1YrS5U-Y8jvy7SgJnz3mizoT-_jpZA6MCrbCAuUrVwCLL7yNdqfwYPuZtfRial4mo5RI5VfPlEQzRrp2KRT1-8)

Here you can see, both are added

![](https://lh4.googleusercontent.com/xYhhjvOp5veM9kYzbU1pxaNeD2o7IYX5ROxYXR1mmqUaIgeQRYnaUnl18qAu14H4oxILZ__KMFVJU7MFvviFAEB87ZIjk-zBqra4toGLa3wgoPzW7W7Yt5JEsvAarKqlnbSWmxBl0tMS2YoaKvWMnvs)

Go the depth then and change the parameters again: 

Start depth: 0.00mm

Final depth:-10.10mm(a bit more then your thickness +0.10mm)

Step down: 1.5mm(½ of your drill bit diameter)

Then just click on apply and OK

![](https://lh4.googleusercontent.com/36BVC-a7ZVohhUISzauoRqTxx53U2UVnUhu2aGqcAeX7aRh4qhNsqBZU54RkkPMdsF--7Oon2P-wIjTPDFAHZQ65jf1xoXGu0Y0zg9hFcrNAIfGeYhMuPjYcnCLCRm-OZQG5PR40mWNN5PdKXrBd4fY)

THen you can go to cam again but no unselect the Pocket_Show, so it only simulate drilling of the holes

![](https://lh6.googleusercontent.com/qS6Qy0CHlWteoFjDssqEpUWirAleaXb-64XaKfehSLwyRH6nqsyP_c4XHdiMUJqy3IQ-ju8Lu78pFyKHm1TzVzvOgXCK9WuOoLDGlXLmDWKWE-rRrDcuMSMgw8rd5R6Bno1ABYlKieO8Pc0MXzdASxo)

If you have this then your almost done, i forgot a step

![](https://lh5.googleusercontent.com/_TXCUDwJ5ultIAl_DEQQv0Fjvfc7Q15OlxX2tFnRDX0D3l-o4nkYHgYwmCiSGCqFCbDJ-SQFaCATWU4cIjAJRlzJaugCBmDdF0Axn9XQJcgFAgXRscu-h5QhvhpCTGvyVmex_KPWI9GPNP8X-TcswjE)

Double click on your drill bit

![](https://lh5.googleusercontent.com/bYFmaAuuGeRfiGQqhMsYGDR9GmMrPJniRcIdUnd4az_OEaUiE8bdkg5q7A2XfVz-fy5RgrVhfWX46NlRniLsvLGkO6IijNA5zFbNr6bI17K5YS2oGuXRYMs43tezvMaGCVf_xTKZIFfG6E8kizqennM)you will come here then

Hozin.Feed: 240.00mm/s

Vert.Feed:80.00mm/s

Spindle:10000

And click on OK

4.5 Cutting the outer edge 
---------------------------

We will continue on the previous project of ours

![](https://lh4.googleusercontent.com/hcMe9W5F0Eg0cFfDLXsaWb3FsNQQE_TXYkNvc_-LFer9sTxt3Ftl6J-EYD-OmhMgJxiRVumW_haXvdX4ZBkRe_a7RxwmIY2KJq_IxSM_HYtAUrlp_EDmxv-1P8rXuiOz1ptk7qagM-eGRtRmwjfy6Pg)

This should have been done the previous time but okay, Go to Job and change the X and Y to 10mm,  Z Stays 0mm

Click on ok after that

![](https://lh5.googleusercontent.com/qsgzdEK0uoUzsTpltVg1Fe8RxKLBKcuAXn0nxgZUakxb72_j84O2kUxtOlxYjXvUihVgkZfjg37HaF18ymyw5sZ5JaC8gF0gS1awtgjO98RhE01UwxOhv_zYLv3ERHAzKQsRoxyrhKbjTs_Etmj0VEk)

THen we create a new profile, and select the top of our base and add it

![](https://lh3.googleusercontent.com/DT_2bDlphlMW5AEWrD1CjhAsQKw36qaiVBvjSz8ejpnwPz_O5laqFWFMR0DAlgS33km6sJZ4iBgqA9V5ZBNcliHcMSvF3a42s_lOH5cuMnPZdXPkDyMNTj9mpgkuoMrqq6LoYvydn7SBjBOfu4cqh80)

Then we go to depth and select these values

Start depth: 0mm

Final depth: -10.10mm

Step down: 1.5mm

![](https://lh4.googleusercontent.com/78pcUJ0k6Tm0eyfuFm8QLMJpYNhk6YrziOa0X_ZeJrMDQL-YhP3_Coh0NivvQVZazCW8-PWHEMIs5Bn09oFe-4W3IAG8ZiQbXEqQdDLrwP50W-wGrrKSxD_80wwaXHlZCUXROovEPj7v_7cgeddskMI)

And make sure its an outside cut

Now we have to add tags: What are tags ? to make sure the piece that we cut doesnt start to move around while we are cutting it 

![](https://lh5.googleusercontent.com/n9_wBVSBabrOSjyv3-R_QpteCPI3ThezilsPCiRcSQ2k1w9U94TKtsmw_BtvXXBOR-fOAYIQtOWKJun5dmn7l5YIsTXAxNLmZSi2qKXyihY_Ouulx4ZS03fTh6iLY6KD75lxQHV9UPAaFMFtPXyfkXE)

To add tags. Select the profile first then go to: PAth->Path Dressup->Tag Dress up

![](https://lh5.googleusercontent.com/xg7OFg2vhQR9BvGveDH0vYxi5Yf0mDEy--IsIuk1sXuTPyKC-IFKMCoOxtlZORKuI_itja4uvfQCv7c-czmqsM8XF2ScridWW_cVoQIkTISqME7-dhcVwQREvKVSSdLRNqXxSbDLa3DRfwDwQPKXcZs)

U will see the coordinated and the location of the tags then, you can adjust them if u wanna, but i am gonna leave them as they are

![](https://lh5.googleusercontent.com/kivM1q0VSCij0h2A15pT0fpiCP6VVwJ1Ax_TRwapREs_N-yf1rEc8xqJmunJ6tADkJj4PFoWDEcblXfadez9eIZ8uwiqkt4CTYbqytoCh9NU59GMBxac0DmqJMuQTYw5Jv590Irygu3U-TImmudta6U)

Then i am gonna simulate it and it should look something like this then

After that we wanted to try dogbone tags, So we created a rectangle hole and putted the tags in there

To create a rectangle check my previous documentation

I am gonna start with the profile for the rectangle

![](https://lh4.googleusercontent.com/mPePdxdCXUR1vbi99eaWye9BxAoepAPNjU1JPXN1zufLSak7iU47veXohErR9z2JL_jsKnnOIJlNHU4w8wfLfgpB7626YAV9UToroxRxC1LSv3b9TAseBqAhVdl21spx2PuIdVpQnN4fnEZ0H57HVJE)

We have to select all the inner edges 1 by 1, and then add them

![](https://lh4.googleusercontent.com/xBP9G6wF3pbKKz5uijRLCi4SnpMvbwvr9ln7I5s9Y05im6ZaupuViWNvbhj0PB7TZqfhXjBa7euX6Ok4zpTiyL8rrORrhZhFU4NFmq00kJA0GkonGf43tBejDuPVvaMPVmhKXm2aMgumnHGkkRoQulE)

We go to depth

Starting depth: 0mm

Final depth: -10.10 mm

Step down: 1.5 mm

![](https://lh3.googleusercontent.com/S8-zBRUNhTYlBVDsC_9Jazn3BVhZwkIHhxAd8T3SUE4i_d-13uDuK5JiUQ_XECLkg6KJ6UDMKReZcQ179oq65_pANe7IbBagn_jkvycH_a2yQZYxk_eJl7WiSbYeuJdXfru_W7spuZXG7uiKTLBZIAY)

Make sure its an inside cut

![](https://lh4.googleusercontent.com/HP__l0PmkNkTV3j1H_GwxlWlQZPBkD7myuSLeZXTutVpiWH11OCM21pcqeiuwyov6v6h7GYQXusVrSQq03vmBR0PNJO64ZVV-tUrzQJV2K18IrbEc5uKI4btowjfalSvzB-KbQyWEql0tUz8ZlOgpoY)

Then we select the rectangle profile and go to path->path dressup-> dogbone tag

Then we will see the coordinates, then we can go simulate it

![](https://lh5.googleusercontent.com/Yy0aNUOpEciE5afBQZ32cYUh-jV19zybaFC3PsjY7TBZ9j1AZahCJ3Ds0ef1gaHrhH-e9P4lIFmsU7OSVOIYHIh8_SH62ABRAFy38EfG2DxCjfUcgVbAC-kxRYSmEV6DSLFkXRuspadqf_HXyEQL274)

The little bit in the outer edge is the dogbone

4.6 Design for the Laser
------------------------

The laser doesnt use 3d design like the 3d printer or the stepcraft, So we need a 2d design for it, To make your own design we can use freecad

We just create a basic square with 2 holes(square) on the sides

![](https://lh6.googleusercontent.com/oYfISsBD19Eu8twfydpj_Hd1OKy9GQetNoEJIllGr2ZMaAdQpTtN455AGOHQTTXlE2YzeanMig80ln3WZxjHoKYPEQQCv-9Q806rcbOjKfBHgtOejgyVSRPY41T-Kb9Mlw7SbYDBQL1TFUYsaCLHlEEOOEGo5Se9OG4AhKgCQDTMTr1qyYzBRF0Pxg)  First we create a basic design

![](https://lh5.googleusercontent.com/OmxEQhwS0PViKH_sBIuT9t2LvIYmMQaC_ytquKCzHfWBRqfwq4t8pkpdYVRtccYg2QtYayKm6tl7iD4s1i0arV0b7MpNDKl6KP19SPoem4TouURVxUsggK8fe2a5RTI798ZItl5J_yrX-2ezQNNn3sf-wSb9yY8dHaHzBA3XM147R9Ntfc7gCObIdw)But we need it in 2D, So we go to Draft and then Modification and Shape 2D, Now we have a 2D design and need to export it

![](https://lh5.googleusercontent.com/NRYOyLrhVDT2hhZKFiSyzhUQ1yCPTFEyuHJJywpxxaknfmQDbUpbqB1_uWQCc29gzwSKYF_Az2j1dfgCNq3c8hHEuyrYjjtfGjRPpWGHpLWvlHAwr8Z8CwUCaQjA53kcOzqjxObBcV8uA7wG4PC1BgHRfN_8IyOHrIlv6oW2DJJtz8ZQiIXcfohkQQ)

File->Export-> save as a Flattend SVG

 After we have the design we need to CAM it

For that we can use inkscape




Makerspace

<https://en.makercase.com/#/>

We can also use makerspace to design a box or something

![](https://lh6.googleusercontent.com/huq-M5k-lRCw1fk9p9yfdB47hpH-BCFBR2x9_qy3JXLvc3e_v5TXK8o6xgIn2WV9iWN2G_fjpFR68gg3Gwzp8TOn0-FCxXllpn1Mfjk2ZIOx38jDT_5wyE_zCdA2eG2g0gvL_5meqckaDaLzM__aGKB11aYWitJsx0tzERF9y_oe3h_zkQ3FvFygBQ)

First we select the type of box, i will take basic box

![](https://lh6.googleusercontent.com/tPY0tfi78Jhb5vYktVOkL17HqhdTRcrqRN-7iZEqNb8aF2dfXJ8ktd_0YfV_mXrxrgL4A6musBPU1_xGBD0dkyLXSjlWErjsLKedrUKiMQ2qRTTaOZU9gti85UgaNdwtQULntadnNC0spEJ8cj5omHqkVUDTCnfuh-ONoRHDRvrbCGvl2GmunNgRKA)

Select milimeters, and the parameters and the rest of the things, those depend

![](https://lh6.googleusercontent.com/-PvKFA0sI1xSPmBfLb7ZLCb7-VgLQoXEyi--94h3Hw7DUeomLD4vP2VxGv07vDjaLvbt-cUQt_GUZdsK4MshX2CMUDDLAclZ5KlyHCEdr3q9-CyCYiLYUaZ4Ofz2RbP7M2fe_nvngHBrUqBKWb6TWrCorxQ6U5gmsHyKAW30lq_2AENY0cfFiOf6rA)and then select download box plans,  go to line formatting then and select cut line width is 0.2 

![](https://lh5.googleusercontent.com/xuYo3cNMcxWUYkic3MUB317RqpfEamhQUlZKx9S6pykBnyIrllQ9gYDQu3gY5jSplH2NJF73XJRLHkoUCtZgw2shnFHEeZlUXJvLDHHYPGtE8oGhhe_8CKp-u_81BAdzFo3YoP1O_FxPUeRtz0DYFgEwEj8PdmejvQRcQp18yVFbBlvNMYxicqoemw)

And then select Kerf and its 0.06 mm




4.7 Inkscape
------------

![](https://lh3.googleusercontent.com/1dGvaGRQWVHMJa0ejfXgJvk03eAS6TBWS2dPzy5gUmgSCkVx1jiHNw42FueZseHUw5lo2O-B_oYTeIqb6SvC6ps31l5U4ISzew9ZOgquRLpYW5y0GjKTyNxm5Kx-bEtYf_Blbs8xhaWqvF1XR5LqaS3TfwiID-Dx60IK2Qw6c9K8UK6DH7aaTSpb8g)

First we launch inkscap and open a New document. 

![](https://lh4.googleusercontent.com/GBaX6YuiJveefYJjS66HK1LvjjgSpS6TVDjnreUrK4MSGBlCY7No5zhESULKKn9W7QtjzNeXH106LaHRDh-ClMPQCbx9K9VIbRkYLmXee6JETBAs1DCTMeCN3Wws-kAYkw0sekdgwu8mCdQk_RpuaOf-n59gPL4aWUmPqLcq7WhEu_HMJE0KAiyfkA)

Then we need to import our SVG, we go to FIle->import-> and select the SVG

![](https://lh4.googleusercontent.com/-l4gGR-eP8fteyaE0vTD2McUVKfok7iq7z3dN14abvrmYaTmqzCmEkdwc4Qq1kfqt-IwqRfibEbhrBIaAvewVbftwNgbl-hByORjJm-X0iXJq0KauxHRg103mMJvLq36jDOEH4BXCjAG14tvnnKwI-z-p80jEjViGwfYMSmEYo8KmGUOkE7JmH5nYQ)

Then our SVG is imported

![](https://lh5.googleusercontent.com/pdN3XD1qY9kbekYUbekmUazt_ExTUGa2mOkjOFjgluAkncJ-SuFyv0xCnUQLdMmY2Tm0I_c0vZki_0aNOeX3nEH0EJlQFIN83Be2iHy-SMZJfscVlDu43O0RXB_IFfTaK4WawYV1TRmTnZ-KO7YwZsek51zynz_f3kIQrnerMfmDcOZCfWzr5yZqkA)

Then we click on the kinda pen icon and open fill and stroke

![](https://lh5.googleusercontent.com/s6XQ_JWlS3QOp2zL--SyCGEgm4zoQ1Q6xawZC7w1lGCqQliIGhFQ3Y1nM7IRygc_qynaWRKg9KE_UxzLL4hefopv_fEL4H7L-lqasuDel7qvh7aPHHkzKIVFcdTT026r8hdDV3cwX2dc8E0Co6PKf7UHSRI7IMW-ZG0Ebt_FBRqdOv_zInWCO_7EwA)

We select our object and if we want to cut it,  we make i bright RED(255,0,0)

If we want a picture engraved on it,  we can do the following 

![](https://lh5.googleusercontent.com/egi4vZNZlro5MNbyNmUdtxOVRKFUQjIfzit87LYcngH2hTIBZ-17uD07zEt8n5UKjZOoN8rwFnF3DJnC1C47ny3Dwh0LtePRK1Z-C1kQDgv8tmGbDC45nr6HqWVf2l15cHlkxZYtOZQFO207BbpHoiPad7Gihex1uIPezQCJ5khTJOxoLPp1tc2LUw)

We can go to File->Import-> and just select the picture

![](https://lh5.googleusercontent.com/SBkqMMxD4AVastmVky-LLzRFTsgPVkMkzIjt-QDVbeLnSKljq2KrJiy_DOeFxniNeXNcqrLPlJJf3z92i_NiCEvBnvfW0ym1xmVDzhp6t3c3GIuoC91JVdRX89v34cdg_B6gNZQK3m-QbzpidkDGYZIIx16xOiwSoWb-R_PjDlfFFr6JYpMgM0ZvAQ)

Then we have our picture, but this isnt ready for caming yet, so we go to Path-> Trace Bitmap

![](https://lh3.googleusercontent.com/CqHewH7aF_ujxGVftgFBoZ4BflJtdsRRU_P8gj17TiKIftzIn-UdTV-fsi7_-V2otlp1TYgyYHnFPGAHd_84qLmYitk_7ycD6OAXadUb6834VYNeqMZl45GKxD0bQIKi5PIMh0eLqhgvrvUXl7UQvqC3yEuvOiGNV59MO17tPAYWcOuSi5d8XrxROg)

Then we will get something like this, ust click on update ![](https://lh4.googleusercontent.com/hVqtEUHg9DD-4XuBQr2AkUkuVi0gbaMB38V0IvGHnlfDvGs71N0-471dqDKfztDFUJ3Ll4wCRDPLlWzH0GjKVFcAutanJAkl-I1OjgnImAPNtJL6mjcYPO7FASOWhyR28sXfZTWQGfocKFvalDhu1bNHWYvj2qQtMTQZyFk_PeU40zNbTYyNjwmNsw)

and if the picture isnt clear just up the Threshold and when good, just click on Apply

![](https://lh5.googleusercontent.com/-CjLh-OvRXys84VTunINUzeedhw_wYPSypxuDqysB22hbJYwJdoBMGPvm6Lq6yiioIts0b60NHjBPTkTFV6H7Gf2hwU-a0dtTCUMUndgQvKQlnsO8RvNBZQf4U381p4f1ykemiDTQxqrDVdU8vjJK8S7dcj7_QeO1IYzRFUSQWc9gqMYCU-0kIW23Q)

Now both pictures are in one, we can just delete the old one and adjust the new one

![](https://lh3.googleusercontent.com/opjbpQpO7ur20jSu9lab1ESffmIkAyyECtKN0sEuzYQcTNFLXd1VgPnXcU9g4R4r1q9QzVIobbK5e6DrNkpBiFaZVld31HY52goa1H2yZ7a2iJX85refAZK8aMubCCAv_7jVdxoE0dCKTSWL-lG28oFJo1JIS4YyULE_CURMmfNpgB-qRPhlTYyTNA)

Like this 

![](https://lh6.googleusercontent.com/tieGzTCvU9XAMLmY9_QDYVeSxADVcYODuzzeZg22SAe0_l3pmgeLtbs-xM-E8dH3NIHgmcvnUV-SuVP8T6DoG8HFJhWtq8Dk7dRkDgs1YHJbGngqNcORncN2d0ARYlDohp4eTyXBKSKjlTUR9hWDhoqnjB7yefADrVibPZBP2ikvQq0wVsNSPIP-Vg)

Then we can Go to FIll and stroke again, but to fill this time and fill it with another color

![](https://lh5.googleusercontent.com/2oFwrM5PEzySDnTkM4NrgR2HZWDz6pkEf_k19LWk6GM7d4n7dm4y5wZ-Sv4vUC4aHkcF5nt63AA_IVhZwX51W2uIYwJfln3mdIBWqpntgdq3pKvhhz_vU-rHBkOGn_sCveBe8C-_a8FRIddWC7POKhXaECae50t5s4Pfu227RGyey58q6RjNSFWPuw)

Then we can save the file, just go to File-> Save as-> and just put ink after the name

<a id="CB5">
Chapter 5:  CNCC</a>
================

5.1: Stepcraft
--------------

We had to design something related to our final project to cnc, so i designed the magnet holder for my submarine

Just 4 pockets in a circle

![](https://lh6.googleusercontent.com/n80RydUDO04oLFkoK20P5rsYZmdbejpkkK36mEsDcqZ-WJSiTwHCQws88ErbJ06Whh2IOPF4mliXOAQ2SGyPFGnw2h5CMJ3CmhaFAulxp5JQfVvvjMzswvXaOkGM-fj5DhVesvVkpQDM_6fhBxylDe5d_PEa9w7xPC_aVK3Eif4nQozjHt58TlmciA)

The diameter of the magnet is 16mm, and the whole diameter is 80 mm.

After that we open the uccnc  stepcraft_840

![](https://lh3.googleusercontent.com/NGvJ4TJmTWuSsYk9PRuAiTWgCox5BXiET-fhr-N_HO1kGksutY59hotZSqHHhDOTJb4wkp171nk69oZWZ5w3zCS89GFwYePj3-tQoW1NsNkMm5zj1ALWcXoq5hBpnSf4DQm0WvpJSdYF7O1_S7xpDtu7cMBfeCXl94ku0ksD_f0Mq7aXmPFtR7Sd_w)

We first press on reset to connect to the stepcraft. And load the uccnc file.

![](https://lh3.googleusercontent.com/kaNwMJ9LjNy0i1A5yn3SBG7uITIs1UbjJELWS-GVkCTN8uY4GOur-_VuaFcdUySxxLu0WVcLvSW8S4EZfoyFl3TyS0d-33LqKg3OnAKzI2mvMxFru0Ql4tZ7ybSSx6QEpq7Ay9_tUpfms0Lv3m44uTZtge2lbJAulnu36LctHNWGqWBzAeCMZXnkfw)

We need to change the feet speed to F1000.000

I can't demonstrate after this with pictures, But i will try to explain

we need to secure our stock to the stepcraft and then

We now have to move the drill bit over our design to check if it will fit 

and need to set our null points, of the Z the null point is on the stock itself. 

Then we need to put the drill bit on 

and the vacuum to make sure it doesn't get dusty.

Notes: 

-   If something goes wrong, press the red button on the side of the cnc

-   Vacuum on the stock as well, to make sure nothing hinders the drill bit

-   The drill needs to be turned on and off manually 

-   Always cnc with your laptop on power

5.2 Laser
---------

Now we are gonna work with the Laser. 

Under here we have the parameters for the laser

|

CUTTING

 |\
 |
|

Power

 |

70

 |
|

Speed

 |

10

 |
|

ENGRAVING

 |\
 |
|

Power

 |

20

 |
|

Speed

 |

70

 |
|

MATERIAL

 |\
 |
|

Slot width

 |

Material-2* kerf

 |
|

Kerf

 |

0.06

 |
|

Line width

 |

0.2

 |

Kerf: (the Thickness of the laser beam when its gonna cut,so have to adjust our design to make sure we get the perfect cut) 

Power: The power of the laser

Speed: The speed which the laser moves with

For that we need a 2D design, We can use Freecad or [makerspace](https://en.makercase.com/#/).

1.  Fill the laser with water on the backside, make sure there is no air in it

2.  And we also adjust the height of the laser 

3.  Turn on the laser controller, NOT THE LASER

1.  ![](https://lh6.googleusercontent.com/NqEN8Pg5gcr2A-cn63TSpqk1sW8AeqkIys7oHAcOS1d1W4Lm31N8BzwmtNRNXNmKcPZ6rHuDWJ1w9E6_PB6oXuYkUgZkvv55yDC9vNRoizM1Neihv5Ci_S7Q6ObLSN81C3WOnFY6TPni_S-zC5Ip3PU-9nXzj2TWWEqJdsgMfTEV6ieobe4ju9Yj4Q)

This is the laser controller, on this we can see all the details that we need,

-   If this is the first time of that day, We pulse the laser to make sure everything is fine

-   First we adjust the laser to the point on the stock that we want to use, and then we pulse it, if the line is too wide, that means the laser is to high or low, so we have to adjust the height again 

-   Then we can send our design to the laser with the usb cable, if u hear a beep and see ur design on the screen ,means ur good to go, if not just try again, or different usb ports

-   And go to the place you want the laser to start cutting at and click on Origin

-   Then we click on Range to check if everything is fine , not too big or small, not going out of stock etc.

-   IF everything is fine, we click on Start

So this is it for the laser, basics, lets get into using it

First we need a design, Check chapter 4.6 and 4.7 For that

![](https://lh5.googleusercontent.com/ezyft21HFH68kO_iPqaeRrAc_viR22UxpKa0e3WvkyZkh6YJKnvhaKRhSWCrfr0Bjmq7p4Kiye1rDF6C5SY5567UO7r6Q7mR3oLII2GtiATHxPsrnHyku_-w9Gy4chg7MhzerbnD6H0YbSJ-NuWq1ryTMKeKVSG2gQJG7c-WuLVcCPPsauIKmHvrFA)

Then we open lightburn and import the files, File->import->select the SVG

![](https://lh3.googleusercontent.com/I_rTC_OLVJV9w9-07azgaNYoDs7BL5swj1Rl1aVGTxPOTD0Uux0WsACw5tF6gz4DYGXAHnlGRtJGyAJB58mLibC6mYLr27d8lbfVaJDyPsrLqtIxsmRJlYZ5NNkjwEu5fhLAIsKSFw797Hw8blfRDH_sZwm62-7X4VRsPjfedOZeOdPZcwkR34vKww)

Put the whole design in the top right corner and as u can see, there is no red color, i made a mistake in the inkscape then, but no worries, BLACK is cutting and GREEN is engraving then, First make sure the cutting color is always on the bottom, 

![](https://lh5.googleusercontent.com/oX2cAMi8owrTpa8WDE8zR7c-04CE8OW93T24aoaTF_6dtavgr63vWDyZ_41GjVeRJ-nCmqGBmkw3FEYRWT-8dRYf5KigCO4OxrWwrQPCn_DTQ6ugBhKPVHOUhnSrsliu-UzWnv7s99R1TbClNKSPtouEwaMK69t3SW2yvIS2DkGc8ykQ1xvA7ix2qg)

LIke this 

![](https://lh6.googleusercontent.com/ocYfYYA5iXQ0Ix5Kde0eKbATufqx_ij3qbvSHUETOztVpVdTEHX1SSyAQ5Y4mt_mran0gvhXguitNrcgpjOCFUVQ9P8Iur8dI3Ym_dEBlo-lOometr8w7AwvTbs1cJiFwXQE36InYa5cU0TdDkreq4peJmTJ9hp2X5u-rsjpoY4GcfUmvePcju8wFQ)

For engraving these parameters are correct, Power 20% and speed 70

![](https://lh4.googleusercontent.com/qIHiRwcIGXhuz_DXb4N1WwGktW_RmH9GQNz1ZFEn7mfLrSL9aVKkgL0eFXzCVU1yhIgNdSTpGyc48fXwGZ2b1kPrx0zuwmEPZfjQehsOHHOoqptSGyCv8RsouAzgw_8BkfvoHmaS01IiUVQKvhhTZT3_hpV1qm4DEdlfjXwj7jsKhg5cjYpK74AWeQ)

For cutting the parameters need to be, Power 70% speed 10

![](https://lh4.googleusercontent.com/9gKZYVleJkMCHBaC-fDo0uKlO-qKk2r3bY0pzdSS8HTUrtwKOgQXgIB7CazRcj31RNseksXbpOkUTPbGgZK94qfj3yLrlZdmlpZQwdJ4MimqMhGRPHe5EC1SkXX6N2ERsZK8eddIHp3bbOl1liPT4N_JiUhAieWiQYqpGOZdvJIzOfRjlPuNz_C9aA)

If all is correct, just click on send

1.  ![](https://lh6.googleusercontent.com/NqEN8Pg5gcr2A-cn63TSpqk1sW8AeqkIys7oHAcOS1d1W4Lm31N8BzwmtNRNXNmKcPZ6rHuDWJ1w9E6_PB6oXuYkUgZkvv55yDC9vNRoizM1Neihv5Ci_S7Q6ObLSN81C3WOnFY6TPni_S-zC5Ip3PU-9nXzj2TWWEqJdsgMfTEV6ieobe4ju9Yj4Q)

This is the laser controller, on this we can see all the details that we need,

-   If this is the first time of that day, We pulse the laser to make sure everything is fine

-   First we adjust the laser to the point on the stock that we want to use, and then we pulse it, if the line is too wide, that means the laser is to high or low, so we have to adjust the height again 

-   Then we can send our design to the laser with the usb cable, if u hear a beep and see ur design on the screen ,means ur good to go, if not just try again, or different usb ports

-   And go to the place you want the laser to start cutting at and click on Origin

-   Then we click on Range to check if everything is fine , not too big or small, not going out of stock etc.

-   IF everything is fine, we click on Start

<a id="CB6">
Chapter 6: Electronic design </a>
=============================

So now we have to make our own arduino or yeah bord using a microcontroller unit(mcu)

For that we use [kicad](https://www.kicad.org/), So how do we begin

First we of course have to download[ kicad](https://www.kicad.org/download/windows/) and some [libraries](http://fabacademy.org/2019/labs/lakazlab/students/julie-sundar/files/week16/kicad.zip). Then we need to install kicad 

6.1 installation and setup 
---------------------------

![](https://lh4.googleusercontent.com/9eHX1EThw6yi9rRgFeAKKN-GNOCKec2sMWLCitF5hy_caiFeWXozdRdeCIADvEVo2KSzCv_A-2g2V9WYKZNFlaMsLOz3nlurTf8gOFYzzdU5sWy4WZ98hVkKeu_WaXymFLL2U3U1V0dic0XLb706HQuNRdexrqtCq8Dc6sqZ1kOS1ShT1mmiFqZ7iA)

 And just click through

![](https://lh4.googleusercontent.com/VvAOZsKwH8HLhi4ZeAqGgP_9QI-z08lFY6UcZci1txf8x0VqJ-StwNOH6xhqNcvE5A-HNVWtFdmw1IcsGwLgqA-MZhwwcWkjgsDgVLTXev5Rlk0D1IWbWrWiqRcvTtPQSLvIcypXXU9yN2OwwC_HBowNknCCeXd0UdmFvrKSEHase-bg_SLNTwggkg)

Then we can take those libraries from the zip and import it in 

C:\Program Files\KiCad\6.0\lib\kicad

![](https://lh4.googleusercontent.com/iY8PEu2TjhI2Esex47olK3iYx5l_fHcBaY2lLX9uj6fZVfla4ew2mpRkEzsIonmTZlNpX7cUOrIRtzPhdEE6gzuwKziaRVuxNMKfig0QzHB866rO1Ad0FGSNPEeRCACWA4ydJ77bp6FaiOQEQVbluNi_SjE1NeRXgABs9n5xFILWnyJOpEerNYjJVA)

After that we can open kicad click on new project and create one

![](https://lh6.googleusercontent.com/me9MAQ3ojaDYZeIzZ1zt8aS-uHjOwfk6dlaPj_1dseXZkth3LtBMcYXBO8h4GrpLhjXulZalmtdmFxVvEW2hEkmGU4nLmLHfMBvg0dwTHOWnBFjR1JdvgX2RPwKVsvTMMmdifGIAvH7vxogstXvJT2w4RKAfazJQkgu7iu79JXyj4oYhRsRPusm45Q)

And we select schematic view

![](https://lh6.googleusercontent.com/tq0vvXyCAcRuTAmH2E0ulD1oHnUfhK4vANMIiOM7HcCiM2C-A0wlSxwKhP7q6lYeWjqVJavVAMS_3LTpJhq93P7WbC8sdNTesdGMEOnAHRs5XpNO72zFJwms_y76KINGZc5XK-abnJPK22UzBFWCR2xFRBSEsDX5t0pyaUYhjeav0zl79WFE7PD6Fg)

And we should get something like this

First we need to import our libraries before we can continue

We go to Preferences-> Manage symbol libraries

![](https://lh5.googleusercontent.com/xCqWzekuHfT_rL4LglJuFqnIzZRMwX1pdULmQyUDhHChj2e9gy-svV5UKHgiRimOB4GHDr34l0GUVX5S44GH6bxx3hiTG8uJlZ7_hwk8jBx032WqviHCErHLe5nYZOsF78A5pfhJNfaiHbt4VNkXuDhS481Rcgq4_uf5_NF8UUUs1A-jfJ_S3w3_2w)

We add a new row

![](https://lh5.googleusercontent.com/KoFCET5uZwYZYIlXG3UAL45yjW_MpqPvH3ceUM8yHfQ8RLkS2CEzkmEoYJR04NgoR6GUw9AnPR0xAN9R3wwaaNU4ZB11k2V5NBzTpUanRDoZz426elMWZ-eEi05ez19TTbKSFD3OGHxqTSMgQPFaP7ys-koaLtsdxEA4iRuQQst8as-u9MT1Oz6Rhg)

Then select browse

![](https://lh3.googleusercontent.com/-XYP2IPOFIUO5Ye0Qw-lFLaT8MZwvfRNy1V2h7TMNJ9Du31HhW9pObu9lBxda8VbFsAI_XaD_qRDJS4oKw_5rppK0RX5MHGwT48CQSpCtP6W-lXk-YQ91XndJXr36L-0Iy5BgIk1Xv49oOVwJ-g__VANZ9JdCP_n2RetnWC81uwZnppuIgG3JCCLOg)

Go to C:\Program Files\KiCad\6.0\lib\kicad and select fab.lib

Okay now we also need to import the libraries to annotate 

![](https://lh6.googleusercontent.com/E1uefZTx1CS_2DrMkjtBA_Otv5cyieOgR4xMQLiwjkhOgTyHy7ysuyO3xf46moJzRN0aJqRkjtS7uls-qc1ngZtxqGP2TmZ3HFjkpJ-1osuPAYnIu9XnqiSrsa8ulK5kbpi-fccZ-zzeLTkCQzE69ECVZ5LX9KpbOk64ASzwx1L8rPenTP49efp6ZA)

We click on Run footprint assignment tool 

![](https://lh3.googleusercontent.com/5laWK1y8MJySLfhs2Qe_idhGsLOxh2U77GA3Gpvi6tj7p6DkDco7dzdwY6JGyBkC9aecrTTHvTofDX9LacsouUlqDb8LrNKa4d5wRnx-mVsDxCeE6x0FyIP92w8Vf5emveUm_UOpMEu_AW2-Ea5LA1k5-c83oFt2q9q42zNBvjZDEcNmu8V-_7Zxdw)

 We click on Preferences-> Manage libraries and click on new and browse

![](https://lh5.googleusercontent.com/2lZcZVVJjD66yXqa_Lpxeh5B5gpOv4dcGGJrVEl734nEucXsCh3HoTmIcJ1tkda4WlsZaU2vdKx7_c3NaFGfSmPgfnNqs_LygQ0rBrnM7ZLzZNDdh62u5K-34WTpg4dZnNoR3yaLtbc1LwUe5ZwxTyNJCwAa5FyfFJLp9K2C0DkChrIB5QUp4jcfIQ)

This time just select the folder fab_pretty and click on select folder

That is it for the installation and setup of the environment

Now to the real work

6.2 Schematic 
--------------

First we have to import everything 

Components that we are gonna use are 

-   1*Atmega328p-a

-   2*capacitors (CAP-US1206)

-   2*Resistors(RES-US1206)

-   1*Led

-   1*Resonator

-   1*Avrisp

-   1*FTDI-SM-HEADER

-   1*6MM-Switch

-   2*6 pin female connectors

-   2*8 pin female connectors

![](https://lh4.googleusercontent.com/Z-bfL3LG0h09DmeHOg1OIgphd0pNT72a7Bo6gGGq9tNtydF8AjvppcZH9YRW85mRxVY4rPOaAGB7iW3Qsu_D8ipvggLVJEPnnb0qjyMhZefPQUeGB1iBD2s8FM-EPODwSHH8nPdqFSif-jwq_9VVQRUKt66j1VtATy5VEAWpcAMjg-542s3XUqgMHw)

Atmega328P-A

![](https://lh6.googleusercontent.com/3-VtEqPm7fhXGcOZIlKAoO-1d3FwEn3PWtxIIzMGmox1bMc4xAW5kMstGx9tQnQ_Z1SKW3oPqWM0KLrql5h83gtqwY6_NR5jl_r6DB58n4oOeYJv_nIyz4FhHuKyzZtbfUZFBQMJgkrHo7vUHJQxtAgU1qfyfXuMOUmEcVMNsbQmZJkql4avZh4ybA)

CAP-US1206

![](https://lh5.googleusercontent.com/xVgKP2wJEghmxqnbycG3rmauajXQY_a2LZnEUlj1Hr1irJht_NjsKengG3vOWMlLHo2k34t10ykY_LmOXFBt2tH3xZHQkgA5GJCXKh1VwQS-RFT-9bukelYtdsb6e1cYpj-8u-qxD4bq0TLEILNi3yPrTRFgXFQs3xyiitH37clpnwSgpo8sN-i5Tw)

Resistors(RES_US1206)

![](https://lh3.googleusercontent.com/ImSJSyYtGxZ_6Wo9hcNj1eFtM_RFIc0aS35ghWAZLdnabNNeNC3z8bmqB43C2qErQrGJEClnMGzK5pzeQ1LdzlKeB8oOa4MIzfkiQ1JQEVaN3pzvh3U54PJifBEOj3ygUtjk6nI75bLHTNatmGaConiVvWg5SNYEPe3HqLK3vqA-JxGquNukGll0Ww)

LED

![](https://lh4.googleusercontent.com/Ohtcdnb_bsbgoyXG76PN8V8iZDC6gjnZHvjoxsnI6s5sws6ZOKOfkXBhGkbei-sdVyMv_qxAEF2YK5kkidKasIE4rL5MG320c-Ggn1LZ4G7D1vE9YF5K7EthATUWvi9PY3VFda8NlNwWSMG7q3ddEi-UTU2p-z1SQhy3gbsz0q9QslLtQNN5hsfGdQ)

RESONATOR

![](https://lh5.googleusercontent.com/5amtwY9qWz-5cbrnVhmD1j-iCsNo_SZqMqR1rfVgjhelNyQcSJ5B46MIibjJz5aFW__cHNh6AozGkBYYSsD_YIlsQ8r3FK8b6YpXkf16OlClRubmcQW3zPbfnt6JP54c4FQZ15V_pZxgC2w7EjN8tjmVB0b0mYKV_HWT0jNmBIwr9xZtEhaekNymXQ)

AVRISP

![](https://lh4.googleusercontent.com/NzK0oXlYRAULD96SET2xILSwfS1F5euRoFZ841_pi7ErHKFWunxKr5gAdZ9vVSOc0r4LwxeHfXEL6k16qXzwoF4gTKY839GZ1EXiC3uJj14rUrrbEj8O1HZaiNCs-82JY-HGlMcJCZF6rZB-wJ7eJle8U_aL8FjN09J9ghgSTu2o0RmsOXCdGEZx3w)

FTDI-SMD-HEADER

![](https://lh3.googleusercontent.com/PCijPN27NdlLmSerdWxs51kByWR1NIn4dEHtvd2Arexf_p4IOg9RKBEnj9L88U9f6mMIm1M3zzQqXH7jYl0H7JN7045wO-bjw58DxgTFOxCGO9yNhs8TjX4okXOFhzapcRqVl0w0Q2CqWUdAu2vkerV-iGGLIk_iKV1tY-RrgaRPsRtafaBQxcLtjw)

6MM_SWITCH6MM_SWITCH

![](https://lh5.googleusercontent.com/88T1QZtSEXSbB_WK9T9vYqjNGQfksL5_CZtG4jZnUYemZT-yNMXVqeApEnWHxrm6Vc2YWFjUM5h8HqunsGVxdy9nKd5sIxzbnFfwktR88B__SjchugT9XseyjbKlBhfaqeTITaQqfR7ewVeEWq9xz2FMYHRDCN2WX3Bz8d4jFvkeZ5VXwnMZyclRkg)

Conn_01x06_Female

![](https://lh5.googleusercontent.com/jbprqS02wPvztB6TnbJNmRHep4C3JbE4Nf_P_8mvYnOwHTrEnDSDpmSKksqr7Iodq924RLS2enRl8IK7yqLdMDW4K7yNhX7HmN59iH5wHI1K4cBDPsKTS_9F5_N5sBsfSn5Nc5fc8yvGASnNoYsOsVL0R4qPbX9blCFUt9VYiTSm4ZFhNDSFD4fI5Q)

Conn_01x08_Female

![](https://lh3.googleusercontent.com/b5mZJ5ZdDkA5k3J7H5uPGhoYexaXvIPoDttmSCNvwORT_Dz3VhvuVRKNLmu8PSneA2hlEFI526ttjB4eupLgPVsRX5UjX9BySvpCahNxBrig1p9wogWT1SbEEh8DXq3nuxNo4KkLpHuRYwtEMc_2sgzbLQEU_lNww7Z_CFKllw16lSgNZvo1XU1p-g)

Once you have everything on the schematic board its time to connect them

![](https://lh6.googleusercontent.com/xptkZujnVRH8atwCu08-P10SLjDsSd549r8iDFVjsAMNvQazzLlGdtviBJCyJzaq4POz-o_WFgUPBobuiqbFYwte9fJ40GLFvu80VW2zdr820pMAD6LRXYwvnBQmexVcREgQlj_EVKsuL_JHN6w3IGrGWtl0MiMzcU1S-YjNhJCO7KQ4Tfzea6clZw)

And we could use this picture as reference, i wont go on how to connect each wire, but start small, i started on the left side and connect one by one, you cant rush this or you will make mistakes

But okay, once everything is connected or wired up, we need to assign footprints 

![](https://lh5.googleusercontent.com/PZ1J89LQdmRzCIeickrQoTIHcJRSBgUk7vqorjAoXeYPdvetD4eGHiDxYlHnxYr5pCOSpxVywIhTGt8nN0mEyoxGlFE7n_uss0_UkoLtol8Wj0oAziMoiw_D-0NEE7lRXNDECe2SrasMrnx03K8sgtIVfwmx8KJW6ZM_Hjs7Y_i4xoxhco9u6mLvqg)

Click on Run footprint assignment tool and then annotate and once here, you can go to fab on the left and the list will pop up on the right, from there select the prints as in here and then click on apply,save & continue. If everything is right, nothing will happen or pop up 

![](https://lh5.googleusercontent.com/_duK5SAH9UcQdZ4hA6Fe0HYmNL2w_DfZzupKBEehW63ZU2GSCUThBQgJN3KwUr3rXWiLJpYS25ECwKb0o4s6hD9MMfo3XdhXORCDCeJugtjmm_6IkAoAuqpbyyfSUV7vdl1FzW4vN16xxeEpAt063jsoLIjFUoH8bKWf6wAymHS75Zi5mkZGwkJeEg)

Then go to file-> Export-> Netlist  and click on export netlist

![](https://lh3.googleusercontent.com/7nQlT9gpNNGqJSzsB5eled8VDotXLrjbOt5QNoecaCCCCItLsqJQbG7dl0CNLEsS-rp6kDgcF0CfBBSs0WkgKXzNto6PWlzZLUx3OMjI4qPX342YZbJkr0TUBh5z3SLFvqC3KUSmW_rjYEZmoACLy9hw7ngWKYm6jxAe-DQCLKdN5KZJp9ec-ndrEQ)then click on the green icon on the top righty, open pcb in board editor

6.3 PCB board editor 
---------------------

![](https://lh4.googleusercontent.com/N1BnkwX1LZ2qKRDFxlh2BgeBuqTTlox9eGkl7XjYiNcV7oyKJ3iQUgw-QQUyBBkPSf6w17G81W1eBwPiH4OuFCkM-BUhUiFyPmQ9XQKwgJIJ5nRTmo12lUSj12Nr04OXFDaN2CPXKqxg3FX1m2zlhDLu9pcUYr5R6VigC0bKMJe8ej3lKBnLxDqpbg)

Welcome to the PBC BOARD EDITOR, also knows as HELLLLLLLL!!!!!!!!!!!!!!!!!!

![](https://lh6.googleusercontent.com/SNLnbKewYwm-L6P4EHSA0kH7pOgkYNoPOrkaeTsOxigF9V70scrOyuX52BEA-EHMIb_YpaFuOe6GoUuREEASuJoriOAkVfUHJEjhXh-FmN2_YEvrW-kN1ZEyfa-mn8zszfQCiNZXqiEtvqIv4XEu1_KSAwid1OnTbw7Uuo89dhpQvlvIIRK9pQ83eg)

GO to File-> Import-> Netlist, Then select the file, click on load en test and then update PCB

![](https://lh4.googleusercontent.com/qhEJT9ze_8Wh2wXqQYeobh4D95hfaSE56KwK7N5k4FKHLLVgKKVttXPFj54IeLFW7TRnhh7sBye4njM31CO6XEJxF5v6FFybSbSN5JJGLTr9aTWTRkCS67UBA1-6H3hzsMG9XMYqMCv-He6VZ5SmUCiJWqogmB0v_9-SEvbsHrLTyMm-6oGDfeYRPw)

THEN you will be stuck with this mess

I cant guide you how to fix this, its a puzzle, you just need to puzzle it out, but here are a few tips

![](https://lh4.googleusercontent.com/5yDhZ5EaHXMVntn0XPcYtoxNr3_ht3Us3oG0j7b35-n7qDnerFwrFWu3840cqnCsA4_kigIPbbgG1dEQUB0n5Wq5dJmA61J9GOBdX6EHO9aeF3TKm85VOoaSQwFk018UrpevQn0DwlqlrKRic-dahC-wtK6xQh2UI8cR3d5V7E4sDDKcTJJuavFrRw)

First move everything out of the way and keep the io's and position them around the board, rotate them etc. Now you have this, much simpler

![](https://lh6.googleusercontent.com/Ibc-6EonnZ4bCTUVGkLJwBElqfXXd6bYo9HBXQPJOFYptJSDRDlpDolCjRYeKtL0aYA9jY0_oGmJMpmHfliTnBQz4pCZ51Uh1o8NLXehzOgYGOwCTe6EljuHmM_kvnmA7wLKh8CY0HEAs7JYu2I90w-0IS4gchF2ef-YXwli98JT05cYSnk4PjD1fQ)

And now connect the io's and bring back the other stuff  and spread them apart, now its just a game of connecting and playing around

In the end i had this 

And now we have to continue with it

<a id="CB12">
Chapter 12: Final Project </a>
=============================


Final documentation

So for my final project, I am building a submarine, So how did i get started and what did to get here as of today its 20-1-2023 10 0 clock at night, So i jumped blindly into this and i had no idea how submarines even work, so i started research on that and found out they work with [ballast tanks](https://qph.cf2.quoracdn.net/main-qimg-29f56dbb281c9c958277c216812a2197), So air is lighter then water,so when there is water in the tank the submarine is heavier and sinks but when there is air in the tank the submarine is lighter, So now my problem, since i am not gonna build a really big submarine, i have around 1kg to play around with or 10N, Almost nothing. Second thing is Communication, i know that wifi signals dont work underwater, so what now, [RADIO](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3355409/),

Physical Build
--------------

But first things first, i can put communication on a hold for a sec, but the ballast tanks are more important, So lets get building i would say

Ballast tanks
-------------

1.  research

2.  Shopping

3.  Logic/ building

### 1.Research

So how do the ballast tanks work, Well from the videos i watched,Most of them fake i found [real one](https://www.youtube.com/watch?v=pUba126uzvU) it looks like they used a syringe, and something to move it somehow

So the problem with this is, that is it a moving part inside a closed space, not that much of an issue, but it has to like extend to the back, so that part kept me busy for a long time. 

### Works: 

But i took a bolt and put it against a wall and saw that if i rotate it around its axis, the bolt it self stays in the same place, but the nut on the bolt, moves itself, so there i had my answer, i had to make the moving part of the syringe the nut and the rest of it the bolt to say so.

2\. So first i bought a like rod on which a nut could like walk and a bunch on nuts and i ordered the [syringe](https://www.amazon.com/EElabper-Converter-Applicator-Experiments-Industrial/dp/B09BVR2V3Z/ref=sr_1_2?crid=3P8S1O6PVXMR1&keywords=giant+syringe+500ml&qid=1674263622&sprefix=giant+syringe+500ml%2Caps%2C172&sr=8-2) from amazon

![](https://lh5.googleusercontent.com/YSGJ_plE-uPE6UibX327g4ugXnJySzicqlsH7RqhnvSAVNFCEVvZhW6Zc5DPBGFi5Ez93sS3jNZP4dyFrHU_AdyeNR5U7_3d_0OyVi9MNScxT4SN6UN1MzaemU-AfcUTbPVy_ZxSNvGzABCMXO7yu_4mtZ3vn2Lh1-t6OPfg450NBGlpDtAsnSwv-7djDQ)![](https://lh3.googleusercontent.com/l8L95Zus2hPaupESUlWFO6J2U13I_POReBRQ6xH8xKzwdToIDcR8clklZy_LZ2zd0VCkwuLdY2uj3GZ8K-FRO8aLvSEkRULmzcbnbfqsWQwaRLMS28dR06vQRZpojQFXiAhSufHDH6bUhYp2G8KoCFHYjxvW7zTBf2rlCfPL7t-YbgOTarx0JoDXEhBNoQ)

3\. So after that i started building with the help of my dad, we did it in like an hour, so we didn't really have any pics of the building, but we have a video of the end result 

<https://drive.google.com/file/d/12Kf_LXws27O5j4G9DfCABOmAb7oNQHuw/view?usp=share_link>

### Final troubleshooting: 

But 2 things that i saw after the build was done is that, i need a fast and high torque motor. Not two of the best combination, but we were using a drill to test the syringe, so i had a broken drill lying around, so i took it apart and used that motor for the pump

So i tried controlling my motor with the l298n, but something was burning, so i turned it off, for the final that i have now, is my ballast tank that i can control with a drill, not the most iot way, but something and here is my final prototype

![](https://lh6.googleusercontent.com/4lcZetUf1Og0cegffK_crd9KCU2CLkWWGcaHJmENYPcKNY090Ycp1j6JaNxjXkH76_arzyziBA05mWLVEOAWvtsmbQ1NJnjY8XDhrJYcU7TxsALEHmSulUMPHOpf7GivWHvueaP7Dxd5lC7o2qgvQrEUful8r7SWPYt72LU-gbdS8f60PjMMzpt2BLaN8g)

Holder
------

So to hold the syringe in the pipe i also have created a design in freecad and lasered it once, 

First i had to measure the diameter of the syringe which is 70mm and the diameter of the pipe is 102mm, So i created my design in freecad

![](https://lh4.googleusercontent.com/nDv14SEDTukk81wkmXrRA1TzlA9Nu0pfRmaVDo_aoJTqaM-CIyGPiPlRVxzTFn4WN6NuFGaID0asZseojhiTcyKndaGSvwNU50FS5LCxay_uetslbQMy1ZqbGkOWRj_6kN4sUj739Egqgl2dHRNLVnXNT1ZgAMQCS0_l6XDVzz9NgoxQ0xZl0JVyPpAZlQ)

So it looks something like this.

So thats for the ballas tanks, Now the movement

I still haven't figured that out and i am kinda lost on that part, So i am still brainstorming on that

Fi

Code
----

So thats that for the physical build, now software based

So my whole submarine will be controlled by a webapp, now lets see how far i got

So i first build the basic movements in the app, ![](https://lh3.googleusercontent.com/wG1mIW9Qcj3FBl6Z3in_EP-vEm7RU6lD9jfuzVpVJBrXmJkpg4Vy-gNrELfKZ0iaDFcFhm0Tu5buN6ttkpYtk2kLdJYOzIcp9s186yWLxQxs-syjPRdDqxIXvUh5tHsOzRNyB-XcunnIXrI0KX9_q-e4pfDXCZqUoZpKBfvLlPdo5YHPhtgs2rn0A4rwXg)

As you can see i have a basic front,back,left, right and its a sub, so also up and down

 And it can call a function on my esp32 

<https://drive.google.com/file/d/1l-SWLY19tTEE1o8wEdGQpien8GGYyn8w/view?usp=sharing>

But i notices that it is giving me trouble, so i think imma need to use an arduino, but i wanted to try the esp32 one more time, so i am gonna test that tomorrow and give the results, and i also updated my dashboard a bit, caused it looked boring ![](https://lh3.googleusercontent.com/V41TuRnrbPcvUelflnYCM8SbC75tMY-PvUzYDJ2FI7Ibw3w1sr3E5rzdZMNQzUD83Bbm97WjDFSF-xR08QzpqkSLden2ogD96u-CAwQA9fSj2D8Wflx4VwkPczfbilFyYXo1GHsxQCgq8Ddyz76Sz62S_z56nU1YWU86M1rzC56kOasAopLXYxFU3lh2qg)

 A bit better i would say, simple enough to understand tho.

So thats the code part.

So here under i put the research links, every website i visited and got something off in here, 

Pictures, videos, documentation, research of other people

Ballast tanks

<https://create.arduino.cc/projecthub/aruna5/autonomous-underwater-vehicle-a7a53a>

<https://qph.cf2.quoracdn.net/main-qimg-29f56dbb281c9c958277c216812a2197>

<https://www.youtube.com/watch?v=pUba126uzvU>

<https://www.youtube.com/watch?v=kEanKJhZvA0>

<https://www.youtube.com/watch?v=O0NUXnxgax8>

Check list: Build ballast tanks

Communicatie

<https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3355409/>

<https://worldbuilding.stackexchange.com/questions/202979/what-radio-wave-frequencies-work-best-for-communication-between-deep-sea-creatur>

<https://www.youtube.com/watch?v=NcLn61cqdak>

<https://www.youtube.com/watch?v=cq5fDZrWNWA>

<https://www.youtube.com/watch?v=zhkN9V1SI-A>

And here under i did some calculations, didn't work out tho, but still

Submarine calculations: 

Fz=m.g

       1*10

     = 10N\
Fw= pgv

    = 1.10.1m3

Oppervlakte cylinder= πr.r.h

1= 3.14.r.r.0.5

h=50cm

r=0.8m= 80cm

h=1m

r=56cm

h=0.5

r=10

Fb = Vs × D × g

3.14.5.5.50=0.003925m3

fw= 0.0157*1*10= 0.517N

Components:

-   servo 3* 60g each

-   Dc motors 1* 100 g

-   Magnets 200g

-   Arduino mega 37g

-   Additional : 200g

 Total weight: 180+100+200+37+200= 717g

Fz=m.g

      0.717.10= 7.17 N

F
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

4.6. CNCC
---------

We had to design something related to our final project to cnc, so i designed the magnet holder for my submarine

Just 4 pockets in a circle

![](https://lh5.googleusercontent.com/7Q9dlKmqYqAwyXAHvzdZu1eZg72NZ2NxOggI3rSYjTrXVRE8qCnjDFMDFxOMBmch57l0efDrYUlG60sYuwwNo_9HsoLKBTVEWtlZNvPCby9SQaQ4VnVkKwH-nuTuFUO-8ug2Za6P2pdHzIjpUBs9kEqX0aYXcmw_b7sItwN01Xz0UTIVix3-plzmEw)

The diameter of the magnet is 16mm, and the whole diameter is 80 mm.

After that we open the uccnc  stepcraft_840

![](https://lh5.googleusercontent.com/URILj2aL4FOPfCmcqFgPKeWA-hjvq1uq6VaY3XcoaVEc4EVrxzySNrY-aoz16J32U_0fiAKjY60WqD8i1zflxvCDCtzspfHld53JVwbWqM5i4zvSytOJXwAVExrK6UDWNtZMDgzSP2XenWkm9JwsE_dDL4Md-VKyTH2rbDLowyP6aFE6SIDw-vLIZA)

We first press on reset to connect to the stepcraft. And load the uccnc file.

![](https://lh6.googleusercontent.com/v13jscjQ5r-RfUqQXhNcjHTMT6Qx67GKNhya-DU9JMwDPMcgYVn5kmKb1h4fw5otUK_8Db5DIpc_pfLc5BRB98-QYZ9rPN7hdZTclSWMCG-7bV77Mq34JWfNtNs8erXQiN9ukulchyrcXvkZWK4peMQ)

We need to change the feet speed to F1000.000

I can't demonstrate after this with pictures, But i will try to explain

we need to secure our stock to the stepcraft  and then

We now have to move the drill bit over our design to check if it will fit and need to set our null points, of the Z the null point is on the stock itself. Then we need to put the drill bit on and the vacuum to make sure it doesn't get dusty.
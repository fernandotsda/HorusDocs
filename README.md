# <img src='horus.png' class='logo'> &nbsp; Horus NMS - Api Documentation 

> ## Open Api's 
---
```
Horus Open APIs are API routes that clients can request from
```

### Base route

**The base rotue is defined as:** 

```
 http://tsda-horus-YOUR_SERVER.sytes.net:PORT/api/open
```

### Final endpoints


<span class="tag post"> POST </span>


```
 /report-manager/datalogger
```

**In order the send a request, you must be prepared to the following parameters**

<!-- tabs:start -->

#### **Headers**

**Required headers**

|   parameter    	   |  value		   | 
| :-------       	   |   :----       | 
| Authorization    	   |  Horus Username  | 
| Content-Type   	   |  application/json | 

**Horus username is a Horus NMS user**

<span class="icons">&#9888; this user must be logged in Report Manager Horus module</span>

#### **Body**

**Request body**

```json
{
  "TEMPLATE_NAME": "Temperatura TSDA",
  "TEMPLATE_TYPE": "DATALOGGER"
}
```

#### **Response**

**Request response example**

```json
{
  "TEMPLATE_NAME": {
  	"NAME": {
  		TSDA TEMPERATURA: ""
  	}
  },
  "INTERVAL": {
  	"FROM": {
  		"30/03/2022 00:00:30": ""
  	},
  	"TO": {
  		"04/04/2022 11:22:27": ""
  	}
  },
  "LATEST_VALUES": {
  	"Temperatura Rack": {
  		"04/04/2022 12:01:17": "30.27"
  	},
  	"Temperatura Flex": {
  		"04/04/2022 12:01:17": "30.27"
  	}
  },
  "ANALYSIS": {
  	"EMPRESA | Temperatura Rack > 24": {
  		"INSIDE CONDITION": "100%"
  		"TIME_IN":"7.11:21:56"  	
  	},
  	"EMPRESA | Temperatura Rack < 25": {
  		"INSIDE CONDITION": "3.65%"
  		"TIME_IN":"06:32:44.5540000"  	
  	}
  }  	  
}
```

<!-- tabs:end -->



> ## Webhooks
---
```
Webhook is a functionality based on the pub-sub concept
```

**Since version 1.4.7, the Horus System is able to send information to different systems or routes. Based on the Webhook concept, Horus NMS sends equipments alarm notification data for those who have subscribed to receive**

**As Webhooks can be treated more as a concept than a functionality, in this documentation we will explain how users can receive Webhooks notifications from Horus Server**

### First case

#### Local Server

**If you have a local Horus Server running on any machine of your possession, follow the steps to integrate the Horus Server with any route of your own**

1. With Horus Server running go to the users section

2. There, choose an user whom will be associated to the Webhooks

3. Go to the API area, at the bottom of the section

4. Add an URI using the following format

```
http://my-application/webhook-route

or

http://my-application:PORT/webhook-route
```

**After all that, the given route will be able to receive notification from Horus Server**


### Second case

#### TSDA Horus Server

**When using TSDA Horus Server, the steps are dastacly reduced**

1. Contact TSDA and inform an user to be associated to the Webhooks


**The user must be a current user of Horus System**



2. Inform TSDA a URI to be reached by Horus Server

**Use the following URI format**

```
http://my-application/webhook-route

or

http://my-application:PORT/webhook-route
```

**Horus Server will send JSON documents as the following example**

### Response

```json
{
  "element_id": "7bc610c0-c142-429a-8830-55e235cff8e6",
  "element_name": "TSDA Flex",
  "element_ip": "127.0.0.1",
  "element_group_name": "TSDA",
  "alert_gen_epoch": "2021-08-25T14:43:40Z",
  "alert_status": "ALARM_HIGH",
  "alert_severity": "CRITICAL",
  "alert_msg": "Temperatura do shelter | ALARM_HIGH",
  "alert_id": "e13f18fc-6897-4a75-9987-882bf132424d",
  "alert_name": "Temperatura do shelter",
  "alert_value": "58.05ºC"  
}
```

### Description

|   parameter    	   |  description   | 
| :-------       	   |   :----       | 
| element_id    	   |  Equipment id  | 
| element_name   	   |  Eqipment name | 
| element_ip    	   |  Eqipment IP | 
| element_group_name   |  Eqipment group in Horus Server | 
| alert_gen_epoch  	   |  Alarm date and time without time zone | 
| alert_status   	   |  Eqipment name | 
| alert_severity  	   |  Alarm priority  | 
| alert_msg		  	   |  Alarm message describing equipment and alarm status | 
| alert_id		  	   |  Alarm Id | 
| alert_name	  	   |  Alarm measure name | 
| alert_value	  	   |  Alarm value that caused the alarm | 


## GitHub pages

**If you reached this documentation in a GitHub repo, take a look at the web page**  [Horus Docs](https://fernandotsda.github.io/HorusDocs/#/)

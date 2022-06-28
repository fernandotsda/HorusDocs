# <img src='horus.png' class='logo'> &nbsp; Horus NMS - Api Documentation 

> ## Open Api's 
---
```
Horus Open APIs are API routes that clients can request from
```

### Base route

**The base route is defined as:** 

```
 https://tsda-horus-YOUR_SERVER.sytes.net:PORT/api/open
```

### Final endpoints


<span class="tag post"> POST </span>


```
 /report-manager/datalogger
```

<!-- tabs:start -->

#### **Headers**

**Required headers**

|   parameter    	   |  value		   | 
| :-------       	   |   :----       | 
| Authorization    	   |  Horus Username  | 
| Content-Type   	   |  application/json | 

**Horus username is a Horus NMS user**

<span class="icons">&#9888; this user must be authorized on Horus Server to access this route</span>

#### **Body**

**Request body**

<table>
<tr>
<th>With interval</th>
<th>No interval</th>	
</tr>
<tr>

<td>

```json
{
"TEMPLATE_NAME": "EMPRESA REDE",
"TEMPLATE_TYPE": "DATALOGGER",
"INTERVAL": "2022-04-30 : 2022-05-30"
}
```			
</td>

<td>

```json
{
"TEMPLATE_NAME": "EMPRESA REDE",
"TEMPLATE_TYPE": "DATALOGGER"
}
```
</td>

</tr>

</table>




#### **Response**

<table>
<tr>
<th>With analysis</th> 
<th>No analysis</th>
</tr>
	
<tr>
<td>

```json
	{
    "TEMPLATE_NAME": {
        "NAME": {
            "VALUE": "EMPRESA REDE"
        }
    },
    "LATEST_VALUES": {
        "Tensão Fase R": {
            "VALUE": "120,13",
            "DATE": "30/05/2022 11:25:41"
        },
        "Tensão Fase S": {
            "VALUE": "119,19",
            "DATE": "30/05/2022 11:25:41"
        }
    },
    "MAX_VALUE": {
        "Tensão Fase R": {
            "VALUE": "128,83",
            "DATE": "26/05/2022 21:20:04"
        },
        "Tensão Fase S": {
            "VALUE": "126,98",
            "DATE": "27/05/2022 06:52:48"
        }
    },
    "MIN_VALUE": {
        "Tensão Fase R": {
            "VALUE": "107,93",
            "DATE": "26/05/2022 17:31:38"
        },
        "Tensão Fase S": {
            "VALUE": "106,19",
            "DATE": "26/05/2022 21:21:05"
        }
    },
    "AVG_VALUE": {
        "Tensão Fase R": {
            "VALUE": "120,73",
            "DATE": ""
        },
        "Tensão Fase S": {
            "VALUE": "120,562",
            "DATE": ""
        }
    },
    "TOTAL_TIME": {
        "Tensão Fase R": {
            "VALUE": "4:21:44:52",
            "DATE": ""
        },
        "Tensão Fase S": {
            "VALUE": "4:21:44:52",
            "DATE": ""
        }
    },
    "INTERVAL": {
        "FROM": {
            "DATE_TIME": "25/05/2022 13:40:49"
        },
        "TO": {
            "DATE_TIME": "30/05/2022 11:25:41"
        }
    },
    "ANALYSIS": {
        "EMPRESA|Tensão Fase R > 121": {
            "INSIDE_CONDITION": "57,52%",
            "TIME_IN": "2.19:43:36.1080000"
        },
        "EMPRESA|Tensão Fase S > 121": {
            "INSIDE_CONDITION": "51,55%",
            "TIME_IN": "2.12:41:35.9910000"
        }
    }
}
```
</td>
		
		
<td>

```json
	{
    "TEMPLATE_NAME": {
        "NAME": {
            "VALUE": "EMPRESA REDE"
        }
    },
    "LATEST_VALUES": {
        "Tensão Fase R": {
            "VALUE": "120,13",
            "DATE": "30/05/2022 11:25:41"
        },
        "Tensão Fase S": {
            "VALUE": "119,19",
            "DATE": "30/05/2022 11:25:41"
        }
    },
    "MAX_VALUE": {
        "Tensão Fase R": {
            "VALUE": "128,83",
            "DATE": "26/05/2022 21:20:04"
        },
        "Tensão Fase S": {
            "VALUE": "126,98",
            "DATE": "27/05/2022 06:52:48"
        }
    },
    "MIN_VALUE": {
        "Tensão Fase R": {
            "VALUE": "107,93",
            "DATE": "26/05/2022 17:31:38"
        },
        "Tensão Fase S": {
            "VALUE": "106,19",
            "DATE": "26/05/2022 21:21:05"
        }
    },
    "AVG_VALUE": {
        "Tensão Fase R": {
            "VALUE": "120,73",
            "DATE": ""
        },
        "Tensão Fase S": {
            "VALUE": "120,562",
            "DATE": ""
        }
    },
    "TOTAL_TIME": {
        "Tensão Fase R": {
            "VALUE": "4:21:44:52",
            "DATE": ""
        },
        "Tensão Fase S": {
            "VALUE": "4:21:44:52",
            "DATE": ""
        }
    },
    "INTERVAL": {
        "FROM": {
            "DATE_TIME": "25/05/2022 13:40:49"
        },
        "TO": {
            "DATE_TIME": "30/05/2022 11:25:41"
        }
    }
}
```

</td>
</tr>

</table>

#### **Response Errors**

<table>

<tr>
<th>User not authorized on Horus Server</th>
<th>User not found on Horus Server</th>
</tr>

<tr>
<td>

```json
{
    "Message": "UNAUTHORIZED"
}
```

</td>

<td>

```json
{
    "Message": "ERROR! USER NOT FOUND"
}
```

</td>

</tr>

<tr>
<th>Template name not set or empty</th>
<th>Template doesn't exist</th>
</tr>

<tr>

<td>

```json
{
    "Message": "ERROR! NO TEMPLATE NAME"
}
```

</td>

<td>

```json
{
    "Message": "ERROR! TEMPLATE DOESN'T EXIST"
}
```

</td>

</tr>
</table>


<!-- tabs:end -->

<hr>

<span class="tag post"> POST </span>

```
 /report-manager/latest-values
```

**This route requests real-time data. For this to happen, a screen must be open in Horus Viewer**

<!-- tabs:start -->

#### **Headers**

**Required headers**

|   parameter    	   |  value		   | 
| :-------       	   |   :----       | 
| Authorization    	   |  Horus Username  | 
| Content-Type   	   |  application/json | 

**Horus username is a Horus NMS user**

<span class="icons">&#9888; this user must be authorized on Horus Server to access this route</span>

#### **Body**

**Request body**

```json
{
"TEMPLATE_NAME": "EMPRESA REDE",
"TEMPLATE_TYPE": "DATALOGGER"
}
```	



#### **Response**

```json
	{
    "TEMPLATE_NAME": {
        "NAME": {
            "VALUE": "EMPRESA REDE"
        }
    },
    "LATEST_VALUES": {
        "Tensão Fase R": {
            "VALUE": "118.39",
            "DATE": "04/04/2022 10:00:40"
        },
        "Tensão Fase S": {
            "VALUE": "118.84",
            "DATE": "04/04/2022 10:00:40"
        }
    }
}
```

#### **Response Errors**

<table>

<tr>
<th>User not authorized on Horus Server</th>
<th>User not found on Horus Server</th>
</tr>

<tr>
<td>

```json
{
    "Message": "UNAUTHORIZED"
}
```

</td>

<td>

```json
{
    "Message": "ERROR! USER NOT FOUND"
}
```

</td>

</tr>

<tr>
<th>Template name not set or empty</th>
<th>Template doesn't exist</th>
</tr>

<tr>

<td>

```json
{
    "Message": "ERROR! NO TEMPLATE NAME"
}
```

</td>

<td>

```json
{
    "Message": "ERROR! TEMPLATE DOESN'T EXIST"
}
```

</td>

</tr>
</table>

<!-- tabs:end -->


> ## Webhooks
---
```
Webhook is a functionality based on the pub-sub concept
```

**Since version 1.4.7, the Horus System is able to send information to different systems or routes. Based on the Webhook concept, Horus NMS sends equipments alarm notification data for those who have subscribed to receive**

**In this documentation we will explain how users can receive Webhooks notifications from Horus Server**

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

**When using TSDA Horus Server, the steps are drastacly reduced**

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

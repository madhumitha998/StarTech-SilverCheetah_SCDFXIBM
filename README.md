# StarTech-SilverCheetah_SCDFXIBM 

## Team Description
Hi all! We are **StarTech**! Our team comprises of 5 members: 
  * Gracia
  * Shawbin
  * Madhu 
  * Nixon
  * Ronald 
 
Although some of us have not met each other in real life, we are glad to have participated in this hackathon. Despite spending countless hours and burning midnight oils on our idea, we believe it will be an unforgettable experience we will surely cherish!

## Introduction
### Problem Statement: Emergency Medical Services
Singapore's population is aging rapidly. [By 2030, one in five people will be aged 65 or older](https://www.population.sg/articles/singapores-silver-age). The elderly are more susceptible to heart attacks, strokes and falling down. Such incidents have a more significant effect on the elderly’s health as compared to the rest of the population. It is therefore critical to detect these incidents early and provide immediate assistance so as to minimise the impact. 

According to the Department of Statistics, [it is estimated that there will be 83,000 elderly who are living alone by 2030](https://www.todayonline.com/voices/more-seniors-living-alone-knowing-and-caring-our-neighbours-should-be-norm). If these incidents happen when they are alone at home, it is **difficult for the elderly to alert others** and for our **Community First Responders (CFR) to enter the home** even if they are alerted of the incident. Hence, our team decided to work on a solution to help streamline the process; from the notification of relevant parties, such as SCDF and the CFR, to the arrival of a CFR to aid in the situation.
### Solution: SilverCheetah
Our solution includes a **wearable IoT device** and a **Smart Strong Box**. The wearable IoT device aids in detecting common accidents such as cardiac arrests and falls based on data such as heart rate and IMU respectively. Once an accident is detected, the device will send an alert to SCDF and CFR. In times of emergency, gaining immediate access to the elderly’s home is crucial. As such, our team proposes a Smart Strong Box to be placed outside the elderly’s home which encapsulates a spare key which can only be unlocked with an auto-generated OTP from SCDF database during emergencies. This OTP is sent together with the name and address of the victim to the CFR once a CFR accepts to respond in myResponder Mobile App.

Throughout this process, SCDF is able to conveniently monitor the victim’s vital signs through the IoT device as well as the situational update through a dashboard in real-time.

## Pitch Video 
Take a look at how SilverCheetah tackles the problem here: https://youtu.be/B3AueijOSbE

## Solution Architecture 
![Solution Architecture](https://github.com/madhumitha998/StarTech-SilverCheetah_SCDFXIBM/blob/master/Images/Architecture%20diagram.jpg)

1. Wearable IoT Device detects an accident and sends data to the IBM IoT Platform
2. The data is stored in the Cloudant Database. 
3. CFR and SCDF are alerted. CFR receives the name, address and Smart Strong Box’s OTP of the alert sender via myResponder Mobile App. SCDF views the data in the dashboard. 
4. CFR and SCDF are dispatched to the alert sender. 
5. CFR accesses the Smart Strong Box using the OTP and attends to the alert sender. 

## Detailed Solution
Take a look at our solution details here: [Detailed Solution](https://github.com/madhumitha998/StarTech-SilverCheetah_SCDFXIBM/blob/master/Detailed%20Solution.pdf)

## Getting Started
### Step 1: Create an IoT app in the IBM Cloud
Walk through the steps in this tutorial to [create a Node-RED and Watson IoT Platform starter app in IBM Cloud](https://developer.ibm.com/tutorials/how-to-create-an-internet-of-things-platform-starter-application/). As a result, you will have a Node-RED Starter Kit application connected to the IBM IoT platform.
### Step 2: Set-up an IoT Device
Refer to step 2 to 4 in this [guide](https://developer.ibm.com/tutorials/create-a-voice-enabled-covid-19-chatbot-using-node-red/). 
### Step 3: Install Node-RED dependencies nodes
Instead of adding the additional packages via Manage Palette, use the IBM Cloud Toolchain and the git repository in IBM Cloud to add the following packages to the package.json. Commit the change and the CI/CD toolchain will restage the CF application.

```bash
"node-red-dashboard":"2.x",
"node-red-node-ui-table":"0.x",
"Node-red-contrib-scx-ibmiotapp":"0.x",
"node-red-node-cf-cloudant":"0.x"
```
### Step 4: Insertion of the data into cloudant
1. There is a comment node indicating the flow of inserting data
2. Remember to check the operation is "insert" and tick “only store msg.payload.object”.
2. At the top right corner, click "Deploy" to save any changes. 
3. Click the box next to the "Insert data" node to inject the data. 

### Step 5: Import and deploy the SilverCheetah flow
1. Import the [SilverCheetah](https://github.com/madhumitha998/StarTech-SilverCheetah_SCDFXIBM/blob/master/Scripts/SilverCheetah_flow.json) flow here. 
![SilverCheetah Flow](https://github.com/madhumitha998/StarTech-SilverCheetah_SCDFXIBM/blob/master/Images/flow.jpg)
2. Make the following changes
![IBM IOT node](https://github.com/madhumitha998/StarTech-SilverCheetah_SCDFXIBM/blob/master/Images/ibm_iot.JPG)
![My respondent node](https://github.com/madhumitha998/StarTech-SilverCheetah_SCDFXIBM/blob/master/Images/myresp.JPG)
![HTTP response node](https://github.com/madhumitha998/StarTech-SilverCheetah_SCDFXIBM/blob/master/Images/http.JPG)
![Insert](https://github.com/madhumitha998/StarTech-SilverCheetah_SCDFXIBM/blob/master/Images/insert.JPG)

## IBM Services Used 
SilverCheetah uses a variety of IBM services. These include [IoT Platform](https://cloud.ibm.com/catalog?search=internet%20of%20things%20platform#search_results), [Cloudant](https://cloud.ibm.com/catalog?search=cloudant#search_results) and [Node-RED](https://cloud.ibm.com/catalog?search=node%20red%20app#search_results ). These tools enable a device to publish its data to the cloud, which our team stores in a database and utilises it to send an alert and data to CFR and SCDF. CFR receives the data in the myResponder Mobile App and SCDF is able to view the data in a dashboard.

![dashboard 1](https://github.com/madhumitha998/StarTech-SilverCheetah_SCDFXIBM/blob/master/Images/cloudant%20dashboard.png) 

Alternatively, we can also store the data published by the device in a relational database, which can be visualised using [Watson Studio](https://cloud.ibm.com/catalog?search=watson%20studio#search_results). Our team has created an additional dashboard to illustrate this point. 

![dashboard 2](https://github.com/madhumitha998/StarTech-SilverCheetah_SCDFXIBM/blob/master/Images/WS%20dashboard.jpg)
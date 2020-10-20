![Safety@Work header](/images/header.png)

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Table of contents
=================

<!--ts-->
- [Table of contents](#table-of-contents)
- [The solution](#the-solution)
  - [Use Cases](#use-cases)
  - [Architecture](#architecture)
  - [Source Code](#source-code)
  - [License](#license)
<!--te-->

The solution
============
SAP Italia has developed an asset to support customers and partners in implementing a system to grant employees' safety, through contact tracing logic.

![Safety@Work Our Target](/images/s@w_target.png)

The content of this GH Org. is intended to be used as a "**starting point**" for implementing a Covid-19 prevention system in SAP's customers environments. To do that, all the artifacts available in the Org. Repositories are fully-featured and ready-to-use: this means, that they can be quickly deployed in a productive environment to immediately gain all below mentioned benefits without any mandatory extension of it.

## Use Cases

As mentioned, **Safety @ Work** (S@W) is a ready-to-use solution. It immediately provides to the customer/partner following use cases coverage:

![Safety@Work use cases (1)](/images/use_cases_1.png)

![Safety@Work use cases (2)](/images/use_cases_2.png)

* **Room Booking** - a responsive web application allows users of Safety @ Work to reserve a particular "space" - e.g. a Meeting room or a common/shared space - for him and his colleagues at a given time. Thanks to scheduling features, in a couple of clicks the user is able to send a reservation request that will be (if needed) approved by a supervisor or Manager;

    ![Safety@Work Room Booking](/images/room_booking.png)

* **Area Booking** - a responsive web application allows user to place a booking request for a given area. The overall flow is quite the same of the one explained in the Room Booking app, with the exception that the user is able to tell the system "hey, I'm going to be in that Area in that day". E.g. reservation of a parking lot for a given date, or reservation of a spot into a certain wing of the office;

    ![Safety@Work Area Booking](/images/area_booking.png)

* **Social Distancing** - thanks to a mobile application, the user is able to maintain a *contact log*, filled with all the contact events that occurr when two instances of the same application (i.e. two different users using S@W app at the same time) are exposed one to each other for a certain amount of time. 

    ![Safety@Work Social Distancing](/images/social_distancing.png)
  
    This contact log is uploaded to the company's safe central cloud storage in order to properly notify all *exposed eployees* once a certain person is certified as *tested positive* for Covid-19. This centralized process, grants that all the sensible informations are threated as anonymous before, during and after an exposure event is fired (i.e. each exposed user won't never know the identityt of the tested positive colleague. Only HR manager get this information, once the employee send to him/her a medical certificate);

* **Crowd Monitoring** - the mobile application is able to communicate both with other instances of the app and [Bluetooth Low Energy (BLE) devices](https://en.wikipedia.org/wiki/Bluetooth_Low_Energy). These devices can be installed within specific *hot sposts*, registered within S@W platform. Thanks to [iBeacon protocol](https://en.wikipedia.org/wiki/IBeacon), the solution is able to collect "*fill level*" of each hot spot.
  
    ![Safety@Work Crowd Monitoring](/images/crowd_monitoring.png)

    As a result, a supervisor user can monitor real-time data flow to gain a 360° overview of Crowd levels in each hot spot, in order to apply (if needed) countermeasures to lower the *risk of exposure* within the company.
    
    It is also possible to monitor *historical data* to check crowd levels by timeframes of a given time range (in the past). This features supports customer in taking decisions about schedules, space/room adjustments, etc...

## Architecture
Safety @ Work includes in its architecture three main components, as depicted in following image.

![Safety@Work Logical Architecture](/images/logical_architecture.png)

More in details, the solution includes:

Component | Target audience | Notes
--------- | --------------- | -----
Mobile App | Company's Employee | an **iOS App** used to keep track of all contact events occurred in a day by a single user
Centralized Cloud | System Admin | central **Secure** cloud storage and business logic, that collects all data and provide business logic to both *mobile* and *backoffice apps*.
Backoffice & Monitor apps | HR Manager | set of backoffice **web apps* used to manage all master data of the solution, to input tested positive employees and monitor both realtime and historical crowd data

From the technical perspective, the scenario is entirely based and build on top of [SAP Cloud Platform (SCP)](https://www.sap.com/products/cloud-platform.html) and native iOS capabilities like [Core Location](https://developer.apple.com/documentation/corelocation/) - to support iBeacon Protocol - and [Core Bluetooth](https://developer.apple.com/documentation/corebluetooth) for distance/contact trace.

Below picture shows all the technical components involved in Safety @ Work scenario.

![Safety@Work Technical Architecture](/images/technical_architecture.png)

* **[SAP HANA](https://saphanacloudservices.com/)** - is the central database that is used to store all events coming from mobile App and provide the calculation logic for real-time and historical data monitoring;

* **[Mobile Services](https://help.sap.com/viewer/70ac991a4f734773b1892a8d0d45eabc/Cloud/en-US/63ee26c20b0d4f438007cd6d93a6b1af.html)** - is the *mobile middleware* that optimise communication between mobile app and back-end business logic;

* **[SCP SDK for iOS](https://developers.sap.com/topics/cloud-platform-sdk-for-ios.html#details/cjmap8zwsflp609320bsvksqs)** - lower the complexity and grants flexibility in integrating a native iOS capabilities - i.e. Core Location, Core Bluetooth and UI Kit - with SAP Cloud Platform services;
  
* **[SCP SDK for Android](https://developers.sap.com/topics/cloud-platform-sdk-for-android.html)** - lower the complexity and grants flexibility in integrating a native Android capabilities with SAP Cloud Platform services;

* **[Portal Service](https://help.sap.com/viewer/ad4b9f0b14b0458cad9bd27bf435637d/Cloud/en-US/5798687972fd4c2bace31c65b47f5587.html)** - provides a central entry point (based on *Fiori Launchpad*) to backoffice users. According to their role, different user types have segregated access to specific *Fiori Applications*;

* **[SCP Workflow](https://help.sap.com/viewer/16e4ca742bd742e98184ef1e53d2ec2d/Cloud/en-US/a3220658f2dc46a48e47614aa2a2c663.html)** - build, run, and manage workflows, from simple approvals to end-to-end processes that span across organizations and apps;

* **[HANA Multi-Target Application](https://www.cloudfoundry.org/blog/accelerating-deployment-distributed-cloud-applications/)** - single package containing all business logic necessary to store/expose data - levaraging HANA native artifacts - and backoffice web apps, built using [SAPUI5 Framework](https://sapui5.hana.ondemand.com/).

## Source Code
Source code of this asset can be found in following two repos:

* **[Safety@Work iOS app](https://github.com/SAP-samples/safety-at-work-ios)** - this repo contains source code of iOS application and all the detailed infos needed to start running the app;

* **[Safety@Work Android app](https://github.com/SAP-samples/safety-at-work-android)** - this repo contains source code of Android application and all the detailed infos needed to start running the app;

* **[Safety@Work SCP Multi-Target App](https://github.com/SAP-samples/safety-at-work-mta)** - this repo contains source code of SCP back-end HANA & Business logic app and all the necessary steps to build, deploy and run the solution in a CloudFoundry environment.
  
## License
License
Copyright (c) 2020 SAP SE or an SAP affiliate company. All rights reserved. This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSE) file.

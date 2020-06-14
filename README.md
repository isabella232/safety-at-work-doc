![Safety@Work header](/images/header.png)

Table of contents
=================

<!--ts-->
   * [Introduction](#Introduction)
     * [Use Cases](#Use\ Cases)
       * **Social Distancing**
       * **Crowd Monitoring**
     * 
<!--te-->

Introduction
============
SAP Italia has developed an asset to support customers and partners in implementing following use cases:

The content of this GH Org. is intended to be used as a "starting point" for implementing a Covid-19 prevention system in SAP's customers environments. To do that, all the artifacts available in the Org. Repositories are fully-featured and ready-to-use: this means, that they can be quickly deployed in a productive environment to immediately gain all below mentioned benefits without any mandatory extension of it.

## Use Cases

As mentioned, **Safety @ Work** (S@W) is a ready-to-use solution. It immediately provides to the customer/partner following use cases coverage:

![Safety@Work use cases](/images/use_cases.png)

* **Social Distancing** - thanks to a mobile application, the user is able to maintain a *contact log*, filled with all the contact events that occurr when two instances of the same application (i.e. two different users using S@W app at the same time) are exposed one to each other for a certain amount of time. 

    ![Safety@Work Social Distancing](/images/social_distancing.png)
  
    This contact log is uploaded to the company's safe central cloud storage in order to properly notify all *exposed eployees* once a certain person is certified as *tested positive* for Covid-19. This centralized process, grants that all the sensible informations are threated as anonymous before, during and after an exposure event is fired (i.e. each exposed user won't never know the identityt of the tested positive colleague. Only HR manager get this information, once the employee send to him/her a medical certificate);

* **Crowd Monitoring** - the mobile application is able to communicate both with other instances of the app and [Bluetooth Low Energy (BLE) devices](https://en.wikipedia.org/wiki/Bluetooth_Low_Energy). These devices can be installed within specific *hot sposts*, registered within S@W platform. Thanks to [iBeacon protocolo](https://en.wikipedia.org/wiki/IBeacon), the solution is able to collect "*fill level*" of each hot spot.
  
    ![Safety@Work Crowd Monitoring](/images/crowd_monitoring.png)

    As a result, a supervisor user can monitor real-time data flow to gain a 360° overview of Crowd levels in each hot spot, in order to apply (if needed) countermeasures to lower the *risk of exposure* within the company.
    
    It is also possible to monitor *historical data* to check crowd levels by timeframes of a given time range (in the past). This features supports customer in taking decisions about schedules, space/room adjustments, etc...


# Rudder

Rudder is an open source, private-cloud Segment alternative built with a focus on Privacy and Security written in Go and React. " https://rudderlabs.com.
 
Main Page
=========

![image](https://user-images.githubusercontent.com/52487451/64673168-0b802180-d48b-11e9-8535-9292eff0aa45.png)

Instructions
============

The docker setup is the easiest & fastest way to try out Rudder. If you like what you see, you can setup the infra on AWS EC2 using our Terraform scripts. Our support for Azure and GCP is coming soon.

1. Checkout this repo
2. Run the command `docker-compose up` to bring up all the services.
3. If you already have a Google Analytics account, keep the tracking ID handy. If not, please create one and get the tracking ID.
4. Go to http://localhost:3000 to set up source and destinations. Add a new source from the dropdown for Android/iOS source definitions. Configure your Google Analytics destination with the tracking ID from step above.

5. We have bundled a shell script that can generate test events. Get the “writeKey” from our app dashboard and then run the following command. Run `./generate-event <writeKeyHere>`
 The script generates a sample event and sends it to the backend container that is running in docker. Based on our destination configuration, the backend will transform the event and forward it to the configured destination.
 
6. You can then login to your Google Analytics account and verify that events are delivered in the correct order.

7. You can use our Android, iOS or Javascript SDKs for sending events from your app.

Source Code
===========

The code is distributed over a few repositories. The following blog post describes the major components of the system

https://rudderlabs.com/rudder-an-open-source-alternative-to-segment/

1. Core Backend. Written in Go
    https://github.com/rudderlabs/rudder-server

2. Transformation Module (which includes functions to convert Rudder Events to Destination specific formats). Written in JS
   https://github.com/rudderlabs/rudder-transformer

3. Rudder clients
   https://github.com/rudderlabs/rudder-client

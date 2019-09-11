# rudder-oss

Rudder is an open-source alternative to Segment written in Go.

Setup
=====

The code is distributed over a few github repositories (links at the end of this README). This repo has the docker scripts to setup and run Rudder.

The docker setup is the easiest & fastest way to try out Rudder. If you like what you see, you can try out and check the performance of real-time events on an AWS EC2 machine with our Terraform scripts. Our support for Azure and GCP is coming soon.


Instructions
============

1. Checkout this repo
2. Run the command `docker-compose up` to bring up all the services.
3. If you already have a Google Analytics account, keep the trackingID handy. If not, please create one and keep it for testing.
4. Go to http://localhost:3000 to set up source and destinations. Add a new source from the dropdown for Android/iOS source definitions. Configure your Google Analytics destination with the right trackingID.

We have bundled a shell script that can generate test events. Get the “writeKey” from our app dashboard and then run the following command.

`./generate-event <writeKeyHere>`

5. “Generate-event” script generates a sample event and sends it to the backend container that is running in docker.    Based on our destination configuration, the backend will transform the event and forward it to the configured destination.

You can then login to your Google Analytics account and verify that events are delivered in the correct order.

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

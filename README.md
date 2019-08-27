# rudder-oss

You can try out a simple version of our product in a few minutes in a dockerized setup on your own machine. If you like what you see, you can try out and check the performance of real-time events on an AWS EC2 machine with our Terraform scripts. Our support for Azure and GCP is coming soon.

Run the command `docker-compose up` to bring up all the services. This will bring up the following services.

If you already have a Google Analytics account, keep the trackingID handy. If not, please create one and keep it for testing.


Go to http://localhost:3000 to set up source and destinations. Add a new source from the dropdown for Android/iOS source definitions. Configure your Google Analytics destination with the right trackingID.

We have bundled a shell script that can generate test events. Get the “writeKey” from our app dashboard and then run the following command.


`./generate-event <writeKeyHere>`

“Generate-event” script generates a sample event and sends it to the backend container that is running in docker.    Based on our destination configuration the backend will transform the event and forward it to the configured destination.

You can then login to your Google Analytics account and verify that events are delivered in the correct order.

Like what you see? Talk to us for a live demo. 


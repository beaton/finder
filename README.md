# The FINDER service

The Finder service is an Alexa Web Service that handles a variety of requests from an Alexa device through customer handlers. The HandlerSpeechlet class extends the Amazon Alexa SDK SpeechletV2 following a factory pattern to instantiate and respond to the request through the appropriate handler:

1. AMAZON.CancelIntent - maps to the AmazonCancelIntentHandler class
2. AMAZON.FallbackIntent - maps to the AmazonFallbackIntentHandler class
3. AMAZON.HelpIntent - maps to the AmazonHelpIntentHandler class
4. AMAZON.StopIntent - maps to the AmazonStopIntentHandler class

and,

5 FindPeople - custom intent created to call a serivce.  In this case, it calls the Google Calendar service to then locate people via their Google Calendar (or any other service you imagine).

## Why not use a Lambda function?

This is a simple Java web application, built with Spring Boot.

Why would I use Spring boot over an AWS Lambda? Well ... I don't get to code much anymore and I wanted a reference implementation of both Spring boot AND an Alexa skill so this is about killing one bird with two stones. 

## Minimum configuration

1. java version "1.8.0_45" (build 1.8.0_45-b14)
2. Apache Maven 3.3.3

hint: if you have a mac, use homebrew to install the above.

## Build/Run

1. $ mvn clean install
2. $ mvn spring-boot:run

Application configuration can be found under /src/main/resources/application.properties

## Supported REST endpoints

GET localhost:8080</br>
GET localhost:8080/snoop</br>
GET localhost:8080/health</br>: heartbeat endpoint to verify health.
GET localhost:8080/quote</br>: Calls the Spring Boot random expression generator. This is just for fun.
POST localhost:8080/find</br>: Called from the com.youi.finder.alexa.config.Configuration servlet and is used to call the HandlerSpeechlet handler factory to process the Alexa request.

/find and POST requests require header: Content-Type = application/json when using Postman.







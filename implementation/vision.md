# Vision for Implementation

## MVP

The proposed MVP for this product would consist of the following features:
* Ability to upload videos with metadata
* Conversion of videos to streamable format
* Legends app where users can:
  * Search for video
  * Stream video

Other features will follow in subsequent iterations as detailed below

## Phase 1: Video Upload

It will be prudent to start our efforts with our video upload app, so that our video curators can begin adding videos to our service as soon as possible. This will involve building all the components detailed in the video-upload docs, in summary:
* Use terraform to create our required AWS assets including:
  * Cognito
  * Upload App Bucket
  * Video Bucket
  * API Gateway, set up to allow access using cognito JWT token
  * Video Metadata Table
  * Required IAM policies and roles  
* Static Upload Website content, including:
  * Login page that calls to cognito
  * Form for entering video metadata
  * Ability to upload file
  * Necessary calls to our Lambdas via API Gateway
* Metadata Lambda built and deployed with serverless
* Upload Lambda build and deployed with serverless
* Manually creating the user pool of video curators in cognito

## Phase 2: Video Conversion

The next phase should be video conversion, as this can then begin the process of getting our videos into a streaming friendly format for use in our Legends App. This will include all components detailed in the video-processing docs, in summary:
* Use terraform to create and manage our required AWS services including:
  * Video Bucket
  * AWS Elemental MediaConvert and associated config
  * Convert Complete CloudWatch Event
  * Content Bucket
  * Required IAM policies and roles
* Start / Finish Convert lambdas deployed with serverless  

## Phase 3: Basic Legends App - MVP

In this phase we will bring online a simplified Legends App for our test users that only allows searching and streaming of video. This will include the following elements from the legends-app docs:
* Use terraform to create and manage our required AWS services including:
  * Amazon Route 53
  * Cognito User Auth
  * API Gateway with routes configured to accept JWT token from Cognito
    * Only the endpoints for stream and metadata will be available in this iteration
  * Video CDN
  * EKS Cluster and ASG for Legends App containers
  * Required IAM policies and roles
* Stream Lambda deployed through serverless
* Metadata Lambda deployed through serverless 
* Legends App with pages for:
  * Logging in
  * Searching for videos
  * Streaming videos
* Manually set up user pool in Cognito for this phase

## Phase 4: Recommendations and Preferences

We can now extend the app to store user preferences and watch data to give them recommendations. This will include the following elements from the legends-app docs:
* Create the Users Table in terraform with necesssary IAM policies and roles
* Recommendation Lambda deployed with serverless
* Add the recommendation lambda endpoints to API Gateway
* Update the Legends App to:
  * Add a screen where a user can store preferences
  * When a user views a video, add it to their watch data in the Users table
  * Add a component which shows the user recommendations based on their preferences, watch history, and popularity of videos

## Phase 5: Video Newsletter

In this phase we will deliver a system for notifying registered users of new videos uploaded in the last week. This will include all components of the video-notification docs, in summary:
* Use terraform to create and manage our required AWS services including:
  * Weekly Cloudwatch event
  * Email Queue
  * Idempotency Table
  * Notify Email SES
  * Required IAM roles
* Notify Lambda deployed with serverless
* Email Lambda deployed with serverless
* Email template designs for the newsletter

## Phase 6: Payment Integration and Signup

Here we would need to implement a payment gateway, such as paypal into our app. Data on subscribed status could be stored in the Users table and be checked as part of our Cognito auth to determine whether a customer has paid. This would also involve allowing user signup from the Legends App, so a sign up page would have to be built that would interact with the Users Table and Cognito.

## Phase 7: Native App

Moving forward we can migrate the app to a React Native framework, and do the encessary tweaks for it to run seamlessly on other devices. We may also want to source our content from Headless CMS at this juncture, to ensure style changes apply to all apps simultaneously.

## Phase 8: Legends API

As we already have our Metadata Lambda set up to interact with the Metadata Table, this API should be a fairly straightforward case of deciding what endpoints we want, adding them to our Metadata Lambda, and forwarding those routes to API Gateway and Route 53. We could then provide customers with API key for them to authenticate with.

# Use MediaConvert for Video Conversion

* Date: 2021-07-15 

## Context and Problem Statement

We want to convert our initial video files into a consistent format that will allow us to stream to most devices via our CDN

## Decision Drivers 

* Cost
* Reliability
* Compatability

## Considered Options

* Don't convert at all
* Proprietary video conversion
* MediaConvert

## Decision Outcome

We have chosen to use MediaConvert as it has excellent and extensible functionality out of the box and the cost for video conversion seems low enough that it is made up for by the data savings we will have from our CDN by using the more efficient streaming format we obtain. This will also allow for better user experience as we can ensure a high quality stream for all of our videos.


<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Three-Tier Web App

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-threetier)

**Author:** R  


---

## Build a Three-Tier Web App

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-compute-threetier_2b3c4d5e)

---

## Introducing Today's Project!

In this project, I will demonstrate how to build a scalable three-tier web app. I'm doing this project to learn how to use AWS services like S3, CloudFront, Lambda, API Gateway, and DynamoDB to create a serverless application with a well-organized architecture.

### Tools and concepts

Services I used were CloudFront, S3, Lambda, API Gateway, and DynamoDB. Key concepts I learned include Lambda functions for serverless compute, API Gateway for managing API requests, DynamoDB for NoSQL storage, and how CORS is configured in API Gateway.

### Project reflection

This project took me approximately 3 hours to complete. The most challenging part was troubleshooting the CORS error between API Gateway and CloudFront. It was most rewarding to see the fully functional three-tier application with dynamic data display.

I did this project today to reinforce my knowledge of building serverless applications with AWS. The project met my goals of learning how to integrate various AWS services into a cohesive web app and troubleshoot common issues like CORS.

---

## Presentation tier

For the presentation tier, I will set up an S3 bucket to store my website's files and use CloudFront to deliver the content globally because this allows for scalable, fast delivery of static content like HTML, CSS, and JavaScript to users worldwide.

I accessed my delivered website by copying the distribution domain name from the CloudFront console and pasting it into my web browser. This allowed CloudFront to serve my website globally, as configured in the presentation tier.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-compute-threetier_3a4b5c6d)

---

## Logic tier

For the logic tier, I will set up a Lambda function to fetch data from a DynamoDB table and use API Gateway to expose this functionality to the outside world because this will handle data retrieval and processing for the app's back-end operations.

The Lambda function retrieves data by using the AWS SDK to query a DynamoDB table for a specific user ID passed in the event's query string parameters. It then returns the user data if found or an error message if no data is available.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-compute-threetier_6a7b8c9d)

---

## Data tier

For the data tier, I will set up a DynamoDB table because it's where we'll store and retrieve user data, enabling our Lambda function to access and deliver the information needed by the front-end via the API Gateway.

The partition key for my DynamoDB table is `userId`, which means each item in the table will be uniquely identified by the `userId`. This allows for quick retrieval of data related to a specific user, ensuring fast and efficient queries.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-compute-threetier_u1v2w3x4)

---

## Logic and Data tier

Once all three layers of my three-tier architecture are set up, the next step is to integrate them by updating the `index.html` file. This allows the frontend to send requests to the API Gateway, which then interacts with Lambda to fetch data from DynamoDB and display it.

To test my API, I copied the API's Invoke URL from the API Gateway console, appended `/users?userId=1`, and ran the URL in my web browser. The results were the data from my DynamoDB table being successfully returned by the API.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-compute-threetier_a112c3d5)

---

## Console Errors

The error in my distributed site was because the script.js file still had the placeholder `[YOUR-PROD-API-URL]` instead of the actual API URL. This caused the request to fail as the frontend was unable to find a valid API endpoint to connect to.

To resolve the error, I updated script.js by replacing the `[YOUR-PROD-API-URL]` placeholder with the actual Invoke URL from API Gateway. I then reuploaded it into S3 because the script.js file needed to be updated on the distributed site to reflect the correct API endpoint.

I ran into a second error after updating script.js. This was an error with CORS because API Gateway wasn't configured to accept requests from the CloudFront URL. The browser blocked the request due to cross-origin restrictions, requiring CORS to be enabled on API Gateway.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-compute-threetier_a1b2c3d5)

---

## Resolving CORS Errors

To resolve the CORS error, I first enabled CORS on the /users resource in API Gateway. I checked both GET and OPTIONS methods, then added my CloudFront domain name as the Access-Control-Allow-Origin value to allow requests from the CloudFront domain.

I also updated my Lambda function because I needed to include the CORS headers in the response. The changes I made were adding the `'Access-Control-Allow-Origin': '*'` header in the response, which allows cross-origin requests from CloudFront.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-compute-threetier_1qthryj2)

---

## Fixed Solution

I verified the fixed connection between API Gateway and CloudFront by refreshing the CloudFront domain and confirming that the data from DynamoDB was successfully displayed on my website, indicating that the CORS error was resolved and the API was functioning properly.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-compute-threetier_2b3c4d5e)

---

---

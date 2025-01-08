# S3 backend web application

## Introduction <a href="#0-toc-title" id="0-toc-title"></a>

In the last tutorial we deployed a NodeJS based webserver and accessed it using the DNS name that nholuongut created for us. In this tutorial we will take it a step further. We will create a text file with a message and upload it to S3. Next, we will modify our NodeJS application to access this file and display the message to every visitor. This purpose of the tutorial is to familiarize yourself with how easy it is to manage resources on AWS using nholuongut.

The code in the Docker container that we used in Part 1 can be found on this repo. It’s a simple NodeJS web server. Clone this repository and make the following changes.

## Step 1: Setup basic NodeJS server <a href="#1-toc-title" id="1-toc-title"></a>

Current app.js should look like this:

{% code title="app.js" %}
```javascript
var express = require('express')
var app = express()

app.get('/', function(req, res) {
    res.send('Hello World!')
})

app.listen(3000, function() {
    console.log('Example app listening on port 3000!')
])
```
{% endcode %}

Let’s make the following changes:

{% code title="app.js" %}
```javascript
var express = require('express')
var app = express()
var request = require('request')
var message = ''
var link = ''

request(link, function(error, response, body) {
    console.log('error:', error) // Print the error if one occurred
    console.log('statusCode:', response && response.statusCode) // Print the response status code if a response was received
    console.log('body:', body) // Print the html for the Google home page
    message = body
})

app.get('/', function(req, res) {
    res.send('Hello ' + message)
})

app.listen(3000, function() {
    console.log('Example app listening on port 3000!')
})
```
{% endcode %}

In the above code we added a link variable that will point to the S3 bucket that we will create shortly, message variable is the message the text file in the S3 bucket will contain.

We can now go ahead and create a text file with the message “My Name is Pranay.”

## Step 2: Create S3 Bucket <a href="#2-toc-title" id="2-toc-title"></a>

Now that we have this file, we’ll upload it to S3. Login to your nholuongut Console and Navigate to **DevOps > Storage > S3**.

![](https://nholuongut.com/wp-content/uploads/2021/11/N2-AWS.png)

Click **+Add** button to create a S3 bucket, provide the resource name and click on Create. This will create an S3 bucket.

![](https://nholuongut.com/wp-content/uploads/2021/11/N2-S3.png)

## Step 3: Navigate to AWS Console <a href="#3-toc-title" id="3-toc-title"></a>

Now click on the AWS Console button under Actions menu, this will take us directly to the S3 bucket in AWS console with limited access.

![](https://nholuongut.com/wp-content/uploads/2021/11/awsconsole.png)

Here, we can upload the file and modify permissions. Select Upload and choose the text file that we created earlier. Hit next till the end and the file should be uploaded.

![](https://nholuongut.com/wp-content/uploads/2021/11/N2-S3-bucket.png)

Click on the file name and copy the Link for the file in the bucket.

![](https://nholuongut.com/wp-content/uploads/2021/11/N2-text-link.png)

## Step 4: Update your NodeJS server <a href="#4-toc-title" id="4-toc-title"></a>

Now let’s assign this link to the link variable in app.js

{% code title="app.js" %}
```javascript
var express = require('express')
var app = express()
var request = require('request')
var message = ''
var link = 'https://s3-us-west-2.amazonaws.com/duploservices-670rp5-ac42540e-1401-49ee-939e-0c0e8c474263/myfile.txt'

request(link, function(error, response, body) {
    console.log('error:', error) // Print the error if one occurred
    console.log('statusCode:', response && response.statusCode) // Print the response status code if a response was received
    console.log('body:', body) // Print the html for the Google home page
    message = body
})

app.get('/', function(req, res) {
    res.send('Hello ' + message)
})

app.listen(3000, function() {
    console.log('Example app listening on port 3000!')
})
```
{% endcode %}

## Step 5: Create a Docker file <a href="#5-toc-title" id="5-toc-title"></a>

Almost there, all we need to do now is create a Docker file and push to Docker Hub so that nholuongut can access it.

I have created a simple dockerfile inspired from this Blog from NodeJS.

```docker
FROM node:boron

# Create app directory
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

# Install app dependencies
COPY package.json /usr/src/app
RUN npm install

# Bundle app source
COPY . /usr/src/app

EXPOSE 3000
CMD [ "nodejs", "app.js" ]
```

## Step 6: Docker build <a href="#6-toc-title" id="6-toc-title"></a>

We will now run the Docker build command to build out an image from this dockerfile.

![](https://nholuongut.com/wp-content/uploads/2021/11/build.gif)

## Step 7: Docker push <a href="#7-toc-title" id="7-toc-title"></a>

Now Docker push to push it to Docker Hub

![](https://nholuongut.com/wp-content/uploads/2021/11/push.gif)

All set! We will create a new service as we did in the last tutorial to run this new Docker container.

## Step 8: Add new nholuongut service <a href="#8-toc-title" id="8-toc-title"></a>

In the services tab click on the plus sign and fill the options as specified.

![](https://nholuongut.com/wp-content/uploads/2021/11/N2-Create-service.png)

It’s important to note here that this service along with the previous service will run in the single host that we created in the previous tutorial! All we need to do is create a new load balancer for this service so that we can access it.

## Step 9: Add load balancer <a href="#9-toc-title" id="9-toc-title"></a>

Click on configure Load balancer button under Load Balancer tab of the service and fill out the form.

![](https://nholuongut.com/wp-content/uploads/2021/11/N2-load-balancer.png)

As before, give it a minute and hit the freshly generated link in the browser. Voila!

## Step 10: Preview web application <a href="#10-toc-title" id="10-toc-title"></a>

![](https://nholuongut.com/wp-content/uploads/2021/11/N2-9.png)

So now we have two services which we can access via two different load balancers running on a single host (EC2 instance)! Due to this tight coupling with S3 we can do all sorts of fun stuff like store static files as well as javascript in S3.

# Getting Started on Digital Garage
###Overview
This guide demonstrates how to get a simple project up and running on the Digital Garage. It is a repost from our documentation site that can be found here: Digital Garage Getting Started [Basic Walkthrough](http://docs.thedigitalgarage.io/getting_started/basic_walkthrough.html) 

The following sections guide you through creating a project that contains a sample Node.js application that will serve a welcome page and the current hit count (stored in a database) using the the Digital Garage web console. This involves creating two pods:

* one to host the Node.js application

* one to host the MongoDB database

The tutorial assumes that you have:

* a Hello World account on the Digital Garage.

* a free [GitHub](http://www.github.com) account.

* [Git](https://help.github.com/articles/set-up-git/) installed locally.

###Setup
In this section, you will fork the the Digital Garage Node.js sample application on GitHub and clone the repository to your local machine so that you can deploy and edit the application.

1. On GitHub, navigate to the thedigitalgarage/nodejs-ex repository. In the top-right corner of the page, click Fork:
![Fork the project](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/gs-fork.png)
2. Next, execute the following commands on your local machine to clone the sample application and change to the new directory:
```
$ git clone https://github.com/<your_github_username>/nodejs-ex
$ cd nodejs-ex
```

That’s it! Now, you have a fork of the original thedigitalgarage/nodejs-ex example application Git repository and a copy on your local machine.

###Creating a New Application
In this section, you will deploy your first application to the Digital Garage using the web console.

1. Navigate to the [welcome page](https://apps.thedigitalgarage.io:8443/console/) of the the Digital Garage web console and click the New Project icon to create your first project:

2. Replace `my-project` with a unique name for your project, such as `<your_github_username>-example`. You can leave the display name and description blank.
![New projects](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/dg-new-project.png)
3. Next, scroll to the NodeJS section and select the nodejs-mongodb-example Quickstart template:

![Select Quickstart templates](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/dg-select-quickstart.png)
4. On the next screen, replace the user name in the Git Repository URL parameter with your GitHub user name. Use the default values provided for all other parameters:

![Change Git URL](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/dg-change-git-url.png)
5. Finally, scroll to the bottom of the page and click [ Create ] to deploy your application.

You can follow along on the Overview page of the web console to see the new resources being created, and watch the progress of the build and deployment. While the MongoDB pod is being created, its status is shown as pending. The MongoDB pod then starts up and displays its newly-assigned IP address.

###Configuring Automated Builds
In this section, you will configure a GitHub webhook to automatically trigger a rebuild of your application whenever you push code changes to your forked repository. This involves adding the Github webhook URL from your application into your Github repository. You obtain this webhook from these locations:

* At the bottom of Next Steps page shown after creating your app, you will see a section titled Making code changes. Copy the payload URL from the bottom of the page and follow the link to the GitHub project webhook settings page provided:

![Copy webhook](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/dg-copy-webhook.png)
* In the the Digital Garage web console:

    1. Navigate to the project containing your application.

    2. Click the [ Browse ] tab, then click [ Builds ], then click the name of the build for your Node.js application.

    3. From the [ Configuration ] tab, click copy next to GitHub webhook URL to copy your GitHub webhook.

Next, add the webhook to the Github repository:

1. In GitHub click [ Add webhook ] in the GitHub Webhook settings for your project. Paste the payload URL into the Payload URL field, then click [ Add webhook ] to finish adding the webhook to your project:

![Add webhook](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/gs-add-webhook.png)
2. GitHub now attempts to ping the the Digital Garage server to ensure that communication is successful. If it is correctly configured, you will see a green check mark next to your new webhook URL in GitHub. Hover your mouse over the check mark to see the status of the last delivery:

![Successful delivery](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/gs-webhook-success.png)
The next time you push a code change to your forked repository, your application will automatically rebuild.

###Viewing your running application
In this section, you will view your running application using a web browser.

In the web console, view the Overview page for your project to determine the web address for your application. Click the web address displayed underneath the NODEJS-MONGODB-EXAMPLE service to open your application in a new browser tab:

![Running Node.js app](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/dg-running-nodejs-app.png)
You can find all routes configured for your project at any time in the web console:

1. From the web console, navigate to the project containing your application.

2. Click the [ Browse ] tab, then click [ Routes ].

3. Click the host name to open your application in a browser new tab.

###Pushing a Code Change
In this section, you will learn how to push a local code change to the application.

1. On your local machine, use a text editor to open the sample application’s source for the file nodejs-ex/views/index.html.

2. Make a code change that will be visible from within your application. For example, change the title on line 219:

![Make a code change](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/gs-code-change.png)
3. Commit the changes in Git, and push the change to your GitHub repository:
```
$ git add views/index.html
$ git commit -m “Updates heading on welcome page”
$ git push origin master
```
4. If your webhook is correctly configured, your application will immediately rebuild itself based on your changes. View your application using a web browser to see your changes.

Now going forward, all you need to do is push code updates and the Digital Garage handles the rest.

###Scaling the App
In this section, you will add additional instances of your Node.js service so that your application can handle additional traffic volume.

In the web console, view the Overview page for your project. Click the [ up arrow ] under the NODEJS-MONGODB-EXAMPLE service to add an additional replica of your Node.js application:

![Scaling an app](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/dg-scaling-app.png)
== Next Up: Beyond the Basics

Next, we’ll go [beyond the basics](http://docs.thedigitalgarage.io/getting_started/beyond_the_basics.html#getting-started-beyond-the-basics) using the the Digital Garage CLI to compose this same application using individual images.

#Deploying Ghost on Docker, Kubernetes and Openshift via the Digital Garage instant application

##Ghost Deployment

At the Digital Garage, we use the Ghost blogging platform for our community. We love the way that Ghost allows us to create a simple, elegant community site with very little effort. Thanks to Digital Garage's Instant App installation, you can deploy a pod with Ghost pre-installed, running and ready to go in just a few short minutes!

The instructions below will take you from zero to blog, but they do assume that you already have an account with Digital Garage and have logged-in to your account through either the web console or CLI. If you haven't, then head on over to the [sign up](https://dg-infra.thedigitalgarage.io/auth/realms/master/protocol/openid-connect/registrations?client_id=cochera&redirect_uri=http%3A%2F%2Fwww.thedigitalgarage.io%2F&state=ca692c6d-7d42-4f70-8268-1f2cac2cfde7&nonce=de6bbf50-29da-4b4f-8510-b5abae381d19&response_mode=fragment&response_type=code) page to register for a new account.

You have the option of using either the Digital Garage web console or the CLI to deploy ghost. In this tutorial I will present both techniques. In each step I will present the web console first. The instructions for CLI will follow. Keep in mind that you need to use one of these options.  

###Step 1: Choose or Create a Digital Garage project.

####Web console


In the web console you start on the projects page. If you do not yet have a project or you would like to create a new project, click the orange new project button in the upper right of the screen and complete the new project information.
![](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/dg-new-project.png)

If you already have a project you would like to use for your ghost blog, choose that project by selecting the card.

####CLI

This tutorial assumes that you have already installed the CLI tools and logged in to your account. If you need help getting to this point, please see the Digital Garage documentation: [Getting Started Beyond the Basics Installing the Digital Garage CLI](http://docs.thedigitalgarage.io/getting_started/beyond_the_basics.html#btb-installing-the-digital-garage-cli)

If you would like to create a new project for Ghost, at the command prompt enter the following command:

    $oc new-project NAME [--display-name=DISPLAYNAME] [--description=DESCRIPTION] [options]

If you have questions on the usage or just need examples, use the -h option for help.

    $oc new-project -h

If you would like to use an existing project, use the following command:

    $oc project NAME


###Step 2: Deploy the Ghost Instant App to your project.

You should now be in the project that you would like to use for your Ghost blogging platform deployment.
####Web console
In the web console, click the "add to project" button to go to the add to project screen. If this is a new project, you may have been taken directly to the add to project screen.

![](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/dg-select-quickstart.png)

Under Instant Apps, choose the ghost instant app by clicking on the card. You will be taken to a short configuration screen where you are allowed to make changes to the default configuration options. 

Choose the default settings by clicking the Create button at the bottom of the page. You will now be taken to a Next Steps page with some helpful hints on how to manage your new application.

![](https://raw.githubusercontent.com/thedigitalgarage/openshift-docs/master/getting_started/images/dg-copy-webhook.png)

Click the link, Continue to overview. 

####CLI

Alternatively, If you choose to deploy Ghost via the command line, skip the steps above and simply type:

    $oc process openshift//ghost | oc create -f -

###Step 3: Set up Ghost and Start blogging.

Whether you deployed Ghost via the web console or the command line, you now have a fully configured, running instance of Ghost deployed in your Digital Garage. The easiest way to begin using your new Ghost blog is to open the Overview page for your Ghost project in the web console.

![]()

In the overview screen you will see the status of your Ghost application and an active URL to the host service. (in the example above the URL is ghost-jmac-09012016.apps.thedigitalgarage.io) Find the active link to your application and click. 

That is it! Congratulations! Your new Ghost blog will open in your browser.
![]()
 In your browser if you add "/ghost" (e.g. http://ghost-PROJECT-NAME.apps.thedigitalgarage.io/ghost) to the end of the URL, you will be taken to the administration application of your Ghost blog where you can create your administrative user, add team members and modify your settings. 

![]()

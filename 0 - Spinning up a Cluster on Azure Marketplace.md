# Lab 0 - Spinning up a Cluster on Azure Marketplace

These are the step-by-step instructions to spin up a Couchbase Cluster on Azure Marketplace.

Navigate to the [Couchbase Enterprise on Azure Marketplace](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/couchbase.couchbase-enterprise). If you have already set up your Azure free account, proceed to the "Get It Now" step below.  Otherwise, click the "Free Account" link.

![Get It Now](/images/0/01SplashScreen.png)

On the subsequent screen, click the "Start free" button.

![Marketplace](/images/0/02FreeAccount.png)

Choose the appropriate license terms (BYOL or Hourly Pricing) and click "Continue" to proceed.

![Create This App](/images/0/CreateThisApp.png)

Next, Azure will start deploying the test drive. This should only take a few minutes.

![Deploying](/images/0a/0103-deploying.gif)

What Azure is doing:
* Deploying 3 "nodes" of Couchbase Server on 3 Azure VMs
* Setting up each node
* Creating a cluster, and adding all 3 nodes to the cluster
* Creating administrator credentials
* Deploying 1 node of Sync Gateway on an Azure VM.

When you use the real Azure Marketplace, it will do all these operations for you as well. However, you will have more control over the deployment. You can configure details like how many nodes, what type of VMs to use, the credentials, and more.

When the test drive is done deploying, you'll see "Access information" displayed.

![Access information](/images/0a/0104-access-information.png)

This includes:

* Server Admin URL (where you'll go in your browser to login to the Couchbase Server Console)
* Admin Credentials (how you'll login to the Console)
* Sync Gateway Admin URL (where you'll go in your browser to view the Sync Gateway console)

You may want to bookmark these URLs and make a note of the access information, since you will be using it throughout the remaining labs.

Great!  Now you're all set to get started with [Lab 1](1%20-%20Logging%20into%20Couchbase.md).

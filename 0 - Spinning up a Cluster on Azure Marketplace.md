# Lab 0 - Spinning up a Cluster on Azure Marketplace

These are step-by-step instructions to spin up a Couchbase Cluster on Azure Marketplace.

Navigate to [Couchbase Enterprise on Azure Marketplace](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/couchbase.couchbase-enterprise). If you have already set up your Azure free account, proceed to the "Get It Now" step below.  Otherwise, click the "Free Account" link.

![Marketplace](/images/0/01SplashScreen.png)

On the subsequent screen, click the "Start free" button.

![StartFree](/images/0/02FreeAccount.png)

Fill in the required "About you" fields.

![SignUp1](/images/0/03Signup1.png)

Azure will need to text you a verification code, so use your cell phone number.

![SignUp2](/images/0/04Signup2.png)

Enter the verification code.

![SignUp3](/images/0/05Signup3.png)

No charge, but you must enter your credit card number.

![SignUp4](/images/0/06Signup4.png)

Agree to the subscription agreeement and click "Sign up".

![SignUp5](/images/0/07Signup5.png)

From here you may be taken to this screen...

![Welcome](/images/0/08Welcome.png)

...or to this one:

![Failed](/images/0/09Failed.png)

Either way, you can easily continue simply by navigating to [Couchbase Enterprise on Azure Marketplace](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/couchbase.couchbase-enterprise).

## Get it Now

Now you can click the "Sign in" link:

![SplashRedux](/images/0/10SplashRedux.png)

Sign in with your Azure credentials...

![Signin](/images/0/11Signin.png)

...and Click the "Get it Now" button:

![GetItNow](/images/0/12GetItNow.png)

Select the Hourly Pricing software plan from the dropdown and click "Continue":

![HourlyRate](/images/0/13HourlyRate.png)

Click "Continue":

![14CreditCard](/images/0/14CreditCard.png)

Now you will create your Couchbase Server administrator credentials and Resource group.  Following the example below, use "labadmin" for your username, and "lab" for your Resource group name.  Set a password as well, then click "OK":

![15Basic](/images/0/15Basic.png)

Now you will configure your Virtual Machine size on Azure.  Click the right arrow next to "Virtual Machine Size"...

![17Config](/images/0/17Config.png)


...to get to the following screen.  Find the DS2_V2 Standard package--you may have to click the "View all" link to find it--and click "Select".

![18Select](/images/0/18Select.png)

Now change your Server Node Count to 2, and your Sync Gateway Node Count to 0, then click "OK":

![19Basic](/images/0/19Basic.png)

...then "OK"...

![20Summary](/images/0/20Summary.png)

...then "Create":

![21Buy](/images/0/21Buy.png)

Now Azure will start deploying your Couchbase cluster. This should only take a few minutes.

![Deploying](/images/0/0103-deploying.gif)

What Azure is doing:
* Deploying 2 "nodes" of Couchbase Server on 3 Azure VMs
* Setting up each node
* Creating a cluster, and adding both nodes to the cluster

When this is done, you will be taken to deployment Dashboard.  Find the Resource Groups link in the left-hand panel and click it:

![23ResourceGroups](/images/0/23ResourceGroups.png)

You will find a link for your lab resource in the main panel.  Click it:

![24Lab](/images/0/24Lab.png)

Now find the Deployments link in the left-hand panel and click it:

![25Deployments](/images/0/25Deployments.png)

You will see a Summary of your deployment, including a link to copy the server admin URL to your clipboard.  Click it:

![26ServerURL](/images/0/26ServerURL.png)

Now you can open a browser tab and paste this link in your address bar.  You will be taken to the Couchbase server admin login screen:

![27Login](/images/0/27Login.png)

You may want to bookmark this URL and make a note of the access information, since you will be using it throughout the remaining labs.

Great!  Now you're all set to get started with [Lab 1](1%20-%20Logging%20into%20Couchbase.md).

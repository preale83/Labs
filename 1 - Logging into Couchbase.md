# Lab 1 - Logging into Couchbase


During this lab you'll login to Couchbase for the first time. You need to complete this lab before starting any of the other labs.

## Objective

This lab is designed to get you started with Couchbase Server. You'll login to the Couchbase Console. In the console, you will load up a bucket of sample data. Finally, you will view the Sync Gateway console.

This lab will not be covering any clients or SDK usage. You will not do anything with the Sync Gateway console in later labs (yet).

## Steps

### Login to the Couchbase Console

Start by going to the Server Admin URL. You will be prompted with a login form. Enter the credentials you received in the last step. Click "Sign In".

![Travel-sample bucket](/images/1/0105-login.png)

Once you successfully login, you will see the Couchbase Enterprise Edition console. You will be looking at the "Overview" section initially. Feel free to navigate around to anything that interests you. Here are a few places of interest to get you started:

* __Server Nodes__ - This will show you a list of all the nodes in the cluster. Each "node" is a separate VM with Couchbase Server installed that joins together into a single "cluster". In a production deployment, you can add nodes to a cluster within the UI, with a command line utility, or with a REST API.
* __Data Buckets__ - In Couchbase Server, a "bucket" is the fundamental data container. Each bucket contains documents. When clicking "Data Buckets", you will see a list of all the buckets that live in the cluster. To start with, the Test Drive has created a single bucket called "sync_gateway". Later, you'll be creating another bucket.
* __Query__ - When you want to run N1QL queries, you can do so from this tab that takes you to the Query Workbench. More on this in [Lab 3 - Querying with N1QL](3%20-%20Querying%20with%20N1QL.md).

### Load "travel-sample" data

In the Couchbase Console, click the "Settings" link.

Once in Settings, click the "Sample Buckets" link. Under "Available Samples", find "travel-sample" and check the box. Click "Load Sample Data" to start loading this sample bucket.

![Travel-sample bucket](/images/1/0106-travel-sample.png)

The "travel-sample" is a set of sample documents that will be loaded into a new bucket called "travel-sample". It contains five different kinds of documents: airlines, airports, routes, hotels, and landmarks. This sample data is meant to help you explore the features and functionality of Couchbase Server. You will use this bucket in the later test drive labs.

![Loading travel-sample bucket](/images/1/0107-loading-travel-sample.png)

The bucket will take a minute or so to completely load. Click on "Buckets" to see a list of all the buckets in this cluster. The "travel-sample" should be on the list now.

When complete, there should be 31,591 documents in the "travel-sample" bucket (look in the 'item count' column).

![Travel sample completely loaded](/images/1/0108-bucket-complete.png)

## Summary

You are now ready to begin labs 2, 3, and 4. The next lab is about [Key Value Document Storage](2%20-%20Key%20Value%20Document%20Storage.md), but you can complete the labs in any order you choose.

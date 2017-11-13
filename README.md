# Labs
## Introduction
The objective of this lab is to familiarize you with the basics of Couchbase Server. After spinning up an instance of Couchbase Server on Azure Marketplace, you will go through four exercises:

1. Couchbase basics
    * You will log into the Couchbase Console (the web-based UI that comes with Couchbase Server)
    * Next, you will load the "travel-sample" bucket, a predefined data set that's great for experimentation.
2. Key/value document storage
    * You will use the Couchbase Console to add documents to a bucket.
    * Next, you will locate documents using the key
    * After that, you will learn how to edit documents.
    * Finally, you will see how to delete a document.
3. Querying with N1QL
    * You will use the Couchbase Console to view indexes on the "travel-sample" bucket.
    * Next, you will execute SELECT queries in the Query Workbench.
    * Finally, you will see how to use data modification queries like INSERT, UPDATE, and DELETE.
4. Full text search (FTS)
    * You will use the Couchbase Console to create a full text search index
    * After creating the index, you will execute the FTS using search terms

## About Couchbase

Couchbase’s mission is to be the data platform that revolutionizes digital innovation. To make this possible, Couchbase created the world’s first Engagement Database. Built on the most powerful NoSQL technology, the open source Couchbase Data Platform includes Couchbase Server and Couchbase Mobile. The platform provides unmatched agility and manageability – as well as unparalleled performance at any scale – to deliver ever-richer and ever more personalized customer experiences.

Couchbase customers include industry leaders like AOL, Amadeus, AT&T, Cisco, Comcast, Concur, Disney, Dixons Carphone, eBay, General Electric, Marriott, Neiman Marcus, Ryanair, Rakuten/Viber, Tesco, Verizon, Wells Fargo, as well as hundreds of other household names.

## Prerequisites

The only prerequisite is a web browser.

In this test drive, a 3 node cluster of Couchbase Server and 1 instance of Couchbase Sync Gateway will be at your disposal.

Note that Sync Gateway is only briefly touched on in this test drive. For more information on using Sync Gateway and the entire Couchbase Mobile solution, please contact [partners@couchbase.com](mailto:partners@couchbase.com) to plan a proof-of-concept.

## Guide to using this test drive

The first lab needs to be done first. After that, you can elect to work on any of the remaining 3 labs in any order.

Code snippets and fields in JSON document will appear as a monospaced font, like this: <code>SELECT t.* FROM \`travel-sample\` t</code>

## What you will learn from this Test Drive

You will learn the basics of using Couchbase Server in this test drive.

Couchbase Server offers a full enterprise document database solution. A performant key/value database engine with a memory-first architecture is at the core of Couchbase Server. The Couchbase Console provides a built-in UI that makes it easy to perform ops and dev tasks out of the box. Couchbase Server also has robust querying options to match your use cases, including [N1QL (which is SQL for JSON)](https://www.couchbase.com/products/n1ql) and a language aware full text search engine built on the [Bleve](http://www.blevesearch.com/) engine. After completing these labs, you will understand how to use all these components.

## Labs

Great.  Now, we're ready to get started!  The test drive labs can be run on either Azure or GCP.  You can even use these lab materials on a cluster you provision yourself.  This is sometimes the case if attending a Couchbase Day.

Instructions on creating a cluster with Test Drive are here:

* [0 - Starting Couchbase on Azure](0a%20-%20Starting%20the%20Azure%20Test%20Drive.md)

With a cluster all ready, here are the labs we'll work through in order:

* [1 - Logging into Couchbase](1%20-%20Logging%20into%20Couchbase.md)
* [2 - Key Value Document Storage](2%20-%20Key%20Value%20Document%20Storage.md)
* [3 - Querying with N1QL](3%20-%20Querying%20with%20N1QL.md)
* [4 - Full Text Search](4%20-%20Full%20Text%20Search.md)

##	Key Takeaways/Summary

**Couchbase basics**: Logging into a cluster. The Couchbase Console makes it easy to view your cluster and perform both dev and ops tasks.

**Key/value document storage**: Documents are keys and JSON values. You can add them quickly, find them by key, make changes by key (as long as it's valid JSON), and delete them by key.

**Querying with N1QL**: Key/value operations will always be the fastest, but querying multiple documents is easy with N1QL (which is just like SQL).

**Full Text Search**: A language-aware search for text is another way to locate document(s). You can leverage the many full text search options to help your users find the information they want.

##	Conclusions and Next Steps

If you're ready, you can visit a cloud Marketplace to spin up your own Couchbase Enterprise cluster. If you'd like to do more research, please check out the [Couchbase Developer portal](https://developer.couchbase.com). If you'd like to try running Couchbase on your own machine, you can [download Couchbase Server Enterprise or Couchbase Server Community](https://www.couchbase.com/downloads) for free. It can run on Windows, Mac, and a variety of popular Linux distros.

##	Contact Information

If you have any questions about Couchbase Server or Couchbase Mobile, please contact [partners@couchbase.com](mailto:partners@couchbase.com).

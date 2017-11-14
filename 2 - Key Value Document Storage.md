# Lab 2 - Key/Value Document Storage

This is the second lab for the Couchbase Test Drive. You need to have completed [Lab 1 - Logging into Couchbase](1%20-%20Logging%20into%20Couchbase.md) before starting this lab.

## Objective

This lab is designed to get you familiar with Couchbase Server. You will learn about buckets, keys and JSON documents work. You will be creating new documents, finding documents by key, making changes to documents, and deleting documents. At the end of this lab, you will understand how to do all those operations within the Couchbase Console.

This lab will not be covering any clients or SDK usage.

## Steps

### Introduction to documents

The fundamental unit of data in Couchbase Server (or any document database) is the document.

Each document is simply a JSON entity. It could be a JSON array, but it is typically a single JSON document. This is an example of a document that is in the travel-sample bucket that you loaded in the previous lab.

```javascript
 {
    "airline": "AF",
    "sourceairport": "TLV",
    "destinationairport": "MRS",
    "airlineid": "airline_137",
    "distance": 2881.617376098415,
    "equipment": "320",
    "stops": 0,
    "type": "route"
    "schedule": [
        {
            "day": 0,
            "flight": "AF198",
            "utc": "10:13:00"
        },
        {
            "day": 6,
            "flight": "AF496",
            "utc": "19:14:00"
        }, ...
    ],
    ...
}
```

This is a document that represents an airline route. It has a number of simple data fields: airline, sourceairport, type, and so on. But it also can store more complex, structured data. The `schedule` field is an array of JSON objects. In a relational database, this would typically be stored as multiple rows in separate table, but it is stored all in one piece in a _denormalized_ form in a document database.

Each document is identified by a "key". In Couchbase Server, that key is not part of JSON object, but it is "metadata". A document key can be any value you want it to be. This document has a key of **route_10000**, for instance.

### What is a bucket?

In Couchbase Server, documents are stored in named **buckets**. Within a bucket, each document must have a unique key. Beyond that, there is no restriction on the shape of the data from document to document. A bucket called **travel-sample**, for instance, could have several thousand airline route documents like the one above, but it could also have hundreds of documents that represent airlines, landmarks, airports, and hotels.

This flexibility is why document databases are said to be "schemaless".

Couchbase Server does not tell individual documents what fields they should or shouldn't have. This is why you often see fields like `type` in the above route example, to act as a sort of discriminator flag for organizational purposes. Although they can be helpful, discriminator fields like `type` are not required, "type" not a reserved word, and the field is not treated any differently in Couchbase than the other fields.

### Create a new document

From the Couchbase Console, click "Buckets".

The "travel-sample" bucket should be listed (it was created in the first lab). Locate it on list of buckets and click the "Documents" link.

![List of buckets in Couchbase Console](/images/2/0201-bucket-list.png)

You should now see a list of documents. The ID column shows the key for each document, and the Content column shows a partial excerpt of the JSON document. To create a new document, click the "Add a Document" link.

![List of documents in a bucket](/images/2/0202-document-list.png)

After clicking the "Add a Document" link, you will be prompted for a document ID. It must be unique to that bucket. If I typed in "airline_10" for instance, I would get an error message. Enter a creative ID like "lab2document" and click "Save Document". A document with that key and some default JSON will be created, and you will be taken to a page where you can make changes to the JSON.

![Edit document](/images/2/0203-edit-document.png)

Enter the following JSON and then click the "Save" button.

```javascript
{
    "name": "Matthew",
    "shoeSize": 13
}
```

If, at any point, the JSON you are entering isn't valid, an error message will appear on the screen. Once you're done, click the "Documents" link to go back to the list of documents. Feel free to experiment and create additional document if you'd like.

### Finding a document by key

This bucket has a large amount of documents. You can go right to a specific document by using its key. Enter the key **route_10000** and click the "Lookup Id" button.

![Lookup document by key](/images/2/0204-lookup-by-key.png)

You should be taken to the document that was shown at the very beginning of this lab. It's an airline route from Ben Gurion Airport in Tel Aviv (TLV) to Marseille Provence Airport in France (MRS). We don't know the name of the airline from looking at just this document, but note that the `airlineid` has a value of **airline_137**. To find out the name of the airline, look up that document by key.

### Make changes to a document

Lookup the document you created earlier (by key **lab2document**). Let's make a change to this document. Let's add something a little more interesting than a flat field:

```javascript
{
  "name": "Matthew",
  "shoeSize": 13,
  "socialMedia": [
      { "twitter": "mgroves" },
      { "github": "mgroves" },
      { "linkedin": "https://www.linkedin.com/in/mgroves/" }
  ]
}
```

Click the "Save" button to make these changes. Notice that I evolved the structure of this data without updating any schema or affecting the other documents in this database. It's possible that some documents have `socialMedia` and some don't. That flexibility/tradeoff makes Couchbase suitable to agile development and to situations where you need to ingest data from multiple sources that have changing data structures.

### Delete a document

Finally, you can delete a document. Just click the "Delete" button from the document list page, or from the individual document editing page.

Note that there are no referential constraints to take into account. If I deleted the **airline_137** document, for instance, the **route_10000** document would still have an airlineid, and it would still have a value of **airline_137**.

## Summary

In this lab, you have learned all the basics of interacting with documents and buckets of documents. You have create a document, edited a document, looked up documents by key, and deleted a document. With this core set of operations and a denormalized data model, you can accomplish some very powerful things.

However, there are situations where key lookups aren't the best approach to finding documents. Please continue with [lab 3 to learn how to query documents with N1QL](3%20-%20Querying%20with%20N1QL.md).

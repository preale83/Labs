# Lab 4 - Full Text Search

This is the fourth lab for the Couchbase Test Drive. This is the second lab for the Couchbase Test Drive. You need to have completed [Lab 1 - Logging into Couchbase](1%20-%20Logging%20into%20Couchbase.md) before starting this lab.

## Objective

This lab is designed to introduce you to the Full Text Search (FTS) capabilities built into Couchbase. With many databases, FTS capabilities are limited or non-existent, and are often farmed out to external tools like Elasticsearch, Solr, etc. Elasticsearch is a powerful tool and Couchbase does have an [Elasticsearch plug-in](https://developer.couchbase.com/documentation/server/current/connectors/elasticsearch-2.2/overview.html) available. For applications requiring search features right within the database itself, however, Couchbase's own FTS (built on the [Bleve](http://www.blevesearch.com/) engine) provides an excellent means of delivering them without any extra integration work.

Couchbase's FTS contains many options for searching and indexing. This lab will only be scratching the surface. You are invited to check out the [extensive FTS documentation](https://developer.couchbase.com/documentation/server/current/fts/full-text-intro.html) once you have a a handle for the basics.

This lab will not be covering any clients or SDK usage.

## Steps

### Search feature

In the "travel-sample" bucket, there are a number of "landmark" documents. These landmarks documents contain information about places, including address, city, geolocation, name, url, and a description (content). Here's an example document (key **landmark_11772**):

```javascript
{
  "name": "The Griddle Café",
  "address": "7916 W Sunset Blvd",
  "url": "http://www.thegriddlecafe.com",
  "content": "The Griddle Café is the best breakfast experience in LA. It features pages of every type of pancake you can imagine, which also happen to be twice as large as any pancake you've ever had, and still manage to be fluffy-thick and light on the tummy. Coffee is fresh, in a French press, and the menu features more than just breakfast. Short story: Food is awesome, service is great, but its always crowded. Don't worry though, they serve fast and you will feel the wait is worth it.",
  "geo": {
    "lat": 34.097866,
    "lon": -118.36221,
    "accuracy": "ROOFTOP"
  },
  "type": "landmark",
  "state": "California",
  ...
}
```

Now put yourself in place of a user trying to find interesting places to go. If that user searches "breakfast", should this document be in the results? What about "bed and breakfast"? Maybe it should appear, but lower down the list in relevancy. What if your user types "brakfast" instead? These type of "language aware" queries that return results with relevancy scores are difficult to do within the more exacting nature of N1QL (or any other SQL variant, as well).

### Building an index

Let's build a index to help our users find interesting results. But let's keep it very simple for this example.

From the Couchbase Console, go to "Search" then click "Add Index".

![Full Text Search indexes](/images/4/0401-indexes-full-text.png)

Let's name the new index "travel-sample-idx". Next, I'll choose the "travel-sample" bucket. After that, let's expand the "Type Mappings" section. There's already a "default" type mapping. If I saved this index now, this index would search on every field in every document (even airline documents, and even the geolocation fields and address fields in landmark documents, which will not be helpful to a user searching for "breakfast").

So, let's narrow it down to just the content field.

Click "Add Type Mapping". Enter "landmark" as the type name. Notice that the "Type Identifier" is set to "JSON type field" with a value of "type". This is the default behavior. But as I mentioned in an earlier lab, there's nothing magical, special, or reserved about the "type" name. You can specify "_type" or "doctype" instead. Let's leave it as "type", since that's what "travel-sample" uses.

Check the box "only index specified field" and click "ok" to save.

![Create index](/images/4/0402-create-index.png)

Next, we need to add a "child field" to this index. Right now, we only want to index the `content` field of landmark documents. Hover over the "landmark" link and click the "+" button. Click "insert child field". Enter "content" as the field and "content" as the "searchable as". Also check the "store" option (more on that later). Click "ok" to save.

After that, uncheck the "default" Type Mapping. We aren't going to use the default index, so this will save time when creating the initial index.

![Create index](/images/4/0403-create-index.gif)

Finally, click the "Create Index" button. This will kick off the initial indexing process. You can watch the progress on the screen (you will see both a "doc count" and an "indexing progress" percentage that will be updated automatically). Since this index is only on "landmark" documents, and only one field within those documents, the indexing should be done quickly. Further changes/additions to documents will be automatically indexed on an incremental basis (or you can manually update if you choose).

### Executing a search

Now that we have a search index, let's try out some searches. We can do this as soon as the index finishes by simply add a search term to the "search this index..." text box. Enter a search term like "breakfast" and click "Search".

![Create index](/images/4/0404-search-breakfast.png)

When searching for "breakfast", you should get 81 results. The most relevant results will appear at the top (just like a web search engine). You can check "Show Scoring" to see the actual score calculations if you'd like.

![Create index](/images/4/0405-search-results.png)

Try search for "breakfast" and then "bed and breakfast". The former returns 81 results, the latter returns 85 results. Also notice that document **landmark_2807** appears in the results of both: 2nd in the former, 4th in the latter.

You can use a variety of operators within the search. You can use `-` to specify that a term must _not_ be in the result, or `+` to specify that a term _must_ be in the result. You can also use the `~` to specify a "fuzziness".

Try these searches and see what happens:

* `+bed -breakfast`
* `-bed +breakfast`
* `brakfast ~2`
* `"bed and breakfast"`

Finally, notice that the search results show a snippet of text with the relevant search terms highlighted (in yellow). When creating this index, you checked the "store" option. If you didn't check that option, you wouldn't get a the snippet and highlight: you would just get the document key and a score.

## Summary

In this lab, you have learned the basics of using Couchbase Server's built in Full Text Search (FTS). You have learned how to create an index, limit the scope of the index, and execute a search.

For a complete reference to all the search options, check out the [bleve documentation](http://www.blevesearch.com/docs/Query-String-Query/) and the [FTS reference](https://developer.couchbase.com/documentation/server/current/fts/full-text-intro.html).

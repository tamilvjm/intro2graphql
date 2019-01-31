# Intro to GraphQL (vs Rest)
Blogathon - Intro to GraphQL (vs Rest)

GraphQL is a query language for your API, and a server-side runtime for executing queries by using a type system you define for your data. GraphQL isn't tied to any specific database or storage engine and is instead backed by your existing code and data.

A GraphQL service is created by defining types and fields on those types, then providing functions for each field on each type. For example, a GraphQL service that tells us who the logged in user is (me) as well as that user's name might look something like this:

type Query {
  me: User
}

type User {
  id: ID
  name: String
}

By the end of this blog, you’ll be able to answer the following questions:

What is GraphQL?
Why are people so excited about GraphQL?
How can GraphQL make my life better?

1. Read Facebook’s GraphQL Intro
This excellent article written by Nick Schrock explains Facebook’s motivation behind creating GraphQL. If this is the first thing you’re reading, skip the part about Relay and go straight to the section on GraphQL. There’s a lot of information there to process, but the most important takeaways are:

GraphQL was designed to solve of the biggest drawbacks of REST-like APIs. You should think of GraphQL as a better alternative to REST.
GraphQL is not a database query language like SQL, it’s an application layer query language that you can use with any backend — SQL, MongoDB, Redis, etc.

REST vs GraphQL

Before the onset of GraphQL, REST was the most widely used architecture for API. Data from the server in a REST system is typically requested using URIs and interfaced with terms. Some of the key REST verbs are HTTP GET, HTTP PUT AND HTTP DELETE. GET is to fetch data from a server in a server-specific format and PUT is used to write data back to the server. All the extra data that is required are fetched using end-points in the REST.

GraphQL is a query language for your API that is nothing like you ever used before. Typically, if you wanted to fetch data from an API that holds book information, you would have a specific endpoint or URL that you are hitting, in this case it would be, exampleURL.com/book/:id. What would be returned is a title, a genre, and maybe some reviews. Now, if you wanted to pull in some data about an author you would have to make another request to another endpoint, exampleURL.com/author/:id, this would return an author name, age, biography, and BookIds. Lastly, if you wanted to receive information about books specific to an author other you would have to make another request. As you can see, we’ve already made three requests to receive basic information. This is the way its been done for a very long time.

REST or Representation State Transfer, has been the way for almost two decades, and before then, XML was king. Typically REST works in the following way:

You make a call from the client to the server using a request method,
HTTP GET requests to fetch data, POST and PUT requests to modify data, and DELETE requests to delete data. These requests are processed by API servers,
and then requested data is sent back in from the server over the HTTP protocol in a format that can easily be handled by computers (JSON).

How does GraphQL differ?
To show the difference between REST and GraphQL, look at the code snippet below. This is query is returning the same information highlighted above.

{
  book(id: "2") {
    name
    genre
    reviews
    author {
      name
      bio
      books {
        name
      }
    }
  }
}
This is just one request! We received all the information we need in just one single HTTP request.

Alternatively, you don’t have to query for all the information, just the information you need.

{
  book(id: "2") {
    name
    author {
      name
      books {
        name
      }
    }
  }
}
In this example, we just want the name of the book, the name of the other, and the names of the books he’s written.


Disadvantages of REST

To read complex data structures requires multiple round trips between the client and server. This causes unnecessary delay mainly considering that most of the mobile applications operate in variable network speeds.
Additional data is fetched by using predefined end-points in REST API. This over time leads to data overload on the client. A REST API with endpoints fetches both the basic data and also the additional data. The client ends up getting what he requires and also the data that is not required. With GraphQL a client can request only the data he requires at that point of time.
REST endpoints are weakly-typed whereas GraphQL is a strongly typed one. A weakly typed query results in data which is not readable by machines and thus tooling is not possible. GraphQL, on the other hand, follows correctness and opens the door for tooling.

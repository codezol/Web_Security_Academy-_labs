## What is GraphQL?
GraphQL is an API query language that is designed to facilitate efficient communication between clients and servers.

## GraphQL scheamas: 
a difinition of available data in a human readable foramt.

## GraphQL queries: 
A way to retrieve data from the data store. similar to api GET requests.

## GraphQL mutations: 
change data in some way, delete adding  or modifing it, similar to POST, PUT and DELETE in APIs.

## Components of queries and mutations:

- Fields: the specification of data that you want to retrieve or modify.(for example firstname and last name are fields)
- Arguments: values provided for specfic field(for example in id:1 1 is the argument)
```graphql
#Example query with fileds and arguments

    query myGetEmployeeQuery {
        getEmployees(id:1) {
            name {
                firstname
                lastname
            }
        }
    }
```
- variables: a way to pass dynamic data into GraphQL queries. 
```graphql
#Example query with variable

    query getEmployeeWithVariable($id: ID!) {
        getEmployees(id:$id) {
            name {
                firstname
                lastname
            }
         }
    }

    Variables:
    {
        "id": 1
    }
```
- Aliases: graphql objects can't contain the same properties, for example the fallowing query is invalid.
```graphql
query getProductDetails {
    getProduct(id: 1) {
        id
        name
    }
    getProduct(id: 2) {
        id
        name
    }
}
```
in this case we can use Aliases
```graphql
query getProductDetails {
    product1: getProduct(id: 1) {
        id
        name
    }
    product2: getProduct(id: 2) {
        id 
        name
    }
}
```

- Fragments: Fragments are reusable parts of queries or mutations. They contain a subset of the fields belonging to the associated type. 

```graphql
fragment productinfo on product { 
    id 
    name
}
```

```graphql
query {
    getProduct(id: 1) {
        ...productinfo
    }
}
```

## Subscriptions:
are a special type of query. They enable clients to establish a long-lived connection with a server so that the server can then push real-time updates to the client without the need to continually poll for data

## introspection:
Introspection is a built-in GraphQL function that enables you to query a server for information about the schema. It is commonly used by applications such as GraphQL IDEs and documentation generation tools.
## Universal queries
If you send query{__typename} to any GraphQL endpoint, it will include the string {"data": {"__typename": "query"}} somewhere in its response. This is known as a universal query, and is a useful tool in probing whether a URL corresponds to a GraphQL service.

## Probing for introspection:
```graphql
 #Introspection probe request

    {
        "query": "{__schema{queryType{name}}}"
    }
```

## Full introspection query: 
```graphql
#Full introspection query

    query IntrospectionQuery {
        __schema {
            queryType {
                name
            }
            mutationType {
                name
            }
            subscriptionType {
                name
            }
            types {
             ...FullType
            }
            directives {
                name
                description
                args {
                    ...InputValue
            }
            onOperation  #Often needs to be deleted to run query
            onFragment   #Often needs to be deleted to run query
            onField      #Often needs to be deleted to run query
            }
        }
    }

    fragment FullType on __Type {
        kind
        name
        description
        fields(includeDeprecated: true) {
            name
            description
            args {
                ...InputValue
            }
            type {
                ...TypeRef
            }
            isDeprecated
            deprecationReason
        }
        inputFields {
            ...InputValue
        }
        interfaces {
            ...TypeRef
        }
        enumValues(includeDeprecated: true) {
            name
            description
            isDeprecated
            deprecationReason
        }
        possibleTypes {
            ...TypeRef
        }
    }

    fragment InputValue on __InputValue {
        name
        description
        type {
            ...TypeRef
        }
        defaultValue
    }

    fragment TypeRef on __Type {
        kind
        name
        ofType {
            kind
            name
            ofType {
                kind
                name
                ofType {
                    kind
                    name
                }
            }
        }
    }
```

## Visualizing introspection results

Responses to introspection queries can be full of information, but are often very long and hard to process.

You can view relationships between schema entities more easily using a GraphQL visualizer. This is an online tool that takes the results of an introspection query and produces a visual representation of the returned data, including the relationships between operations and types. 
```
type Document {
  id: String!
  type: String!
  number: String!
  issueDate: String!
  expiryDate: String!
}

type Relative {
  id: String!
  relationType: String!
  name: String!
  age: Int!
}

type Client {
  id: String!
  name: String!
  age: Int!
  documents: [Document!]!
  relatives: [Relative!]!
}

type Query {
  client(id: String!): Client
}

query ClientAndDocuments($id: String!) {
  client(id: $id) {
    id
    documents {
      id
    }
  }
}

query ClientAndRelatives($id: String!) {
  client(id: $id) {
    id
    relatives {
      id
    }
  }
}

query ClientAndRelativesAndDocuments($id: String!) {
  client(id: $id) {
    id
    relatives {
      id
    }
    documents {
      id
    }
  }
}
```
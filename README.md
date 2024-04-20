<h1 align="center">
   <a href="#"> gRPC with Evans </a>
</h1>

<h3 align="center">
    Using gRPC with Evans and Golang.
</h3>

<h4 align="center"> 
	 Status: Finished
</h4>

This project is divided into one part:
1. Backend

![image](https://github.com/renatafborges/gRPC/assets/63026376/7734707e-7e66-43c3-8c58-84f3df71664e)

### Pre-requisites

Before you begin, you will need to have the following tools installed on your machine:

- [Git] (https://git-scm.com)
- [Golang] (https://go.dev/doc/install)
- [VSCode] (https://code.visualstudio.com/) In addition, it is good to have an editor to work with the code.
- [gRPC] ([https://go.dev/doc/install](https://grpc.io/docs/languages/go/quickstart/)) Follow the Quick Start and install all plugins.
- [Evans-gRpc-Client] (https://github.com/ktr0731/evans)

#### Running Project

```bash

# Clone this repository
$ git clone https://github.com/renatafborges/gRPC

# Create database
$ sqlite3 db.sqlite
sqlite> create table categories (id string, name string, description string);

# Run main.go to up gRPC server
$ go run cmd/grpcserver/main.go  

# In another terminal:
$ evans -r repl

# Select package
$ package pb

# Select service
$ service CategoryService

# To Create a new Category
$ call CreateCategory

# Insert Category Description
$ Notebooks and Computers

# Insert Category Name
$ Computers

{
  "description": "Notebooks and Computers",
  "id": "2e151f7b-f579-49c6-838b-d4793b5d5609",
  "name": "Computers"
}

# To List Categories
$ call ListCategories

{
  "categories": [
    {
      "description": "Cat 1 description",
      "id": "2d9ad836-509e-41fe-86d0-4fe9621fe273",
      "name": "Cat 1"
    },
    {
      "description": "Cat 2 desc",
      "id": "0c25fe2c-9a17-4643-8316-0c391928eb0f",
      "name": "Cat 2"
    },
    {
      "description": "Desc 1",
      "id": "9bd61479-a3a7-490e-95fc-1f836ccea5b0",
      "name": "Cat stream 1"
    },
    {
      "description": "Desc 2",
      "id": "eafe082f-4975-4dd8-bc1d-27d4ba14f23f",
      "name": "Cat stream 2"
    },
    {
      "description": "Desc 3",
      "id": "6a66c136-a4f7-4bca-9b58-0fdec6cf9580",
      "name": "Cat stream 3"
    },
    {
      "description": "cat 1",
      "id": "616db866-7138-4d09-af5a-b61d69994abb",
      "name": "Cat 1 bi"
    },
    {
      "description": "cat 2",
      "id": "0f7bdd57-cb3b-4c9f-a026-d46d7f521b41"
    },
    {
      "description": "Cat 3",
      "id": "006bb1e0-e4c4-4f08-96ac-aa66fa1d5130",
      "name": "Cat 3"
    }
  ]
}

# Searching one Category
$ call GetCategory

# Insert Category Id (for example)
$ 2d9ad836-509e-41fe-86d0-4fe9621fe273

{
  "description": "Cat 1 description",
  "id": "2d9ad836-509e-41fe-86d0-4fe9621fe273",
  "name": "Cat 1"
}

# Working with Stream
$ call CreateCategoryStream
name (TYPE_STRING) => Category Stream 1
description (TYPE_STRING) => Category Stream desc 1
name (TYPE_STRING) => Category Stream 2
description (TYPE_STRING) => Category Stream desc 2
name (TYPE_STRING) => Category Stream 3
description (TYPE_STRING) => Category Stream desc 3

CTRL + D to exit

  "categories": [
    {
      "description": "Category Stream desc 1",
      "id": "d532b62b-dca6-4c2d-a590-7ad014f024e3",
      "name": "Category Stream 1"
    },
    {
      "description": "Category Stream desc 2",
      "id": "5f2566fd-58d3-40e2-ac8e-b6e00f25e7d7",
      "name": "Category Stream 2"
    },
    {
      "description": "Category Stream desc 3",
      "id": "156dee5a-ae1a-4006-882c-6cd0e0a01465",
      "name": "Category Stream 3"
    }
  ]
}

# Working with Bidirectional Stream
$ call CreateCategoryStream
name (TYPE_STRING) => Category Stream Bi 1
description (TYPE_STRING) => Category Stream Bi desc 1
name (TYPE_STRING) => {
  "description": "Category Stream Bi desc 1",
  "id": "2e553f32-ddb3-406a-bc5c-9f851d427874",
  "name": "Category Stream Bi 1"
}

```
## Author
Made with love by Renata Borges 👋🏽 [Get in Touch!](Https://www.linkedin.com/in/renataborgestech)
---

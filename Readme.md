# The non-coding code test

The purpose of this 'code test' is to set the scene for an in-person interview. 

Think about how you would approach the task and be ready to describe and discuss the decisions. We want to find out how you think, how you approach problems and how you communicate your decision and solutions.

NOTE: **don't actually build the code**. What you should do:

1. Imagine you have received this task as a JIRA and think about how you are going to build it.
2. You may like to make a dot-point list about how you would build the code, to help you remember the details in the interview.

As a rough guide, we don't expect you to spend more than about 15 minutes reading through the challenge and thinking about your approach.

# The Core Task/Challenge

## MVP / Version 1

The MVP task is to create the base implementation of an application to view a list of documents:

  - An API has been defined that will return a list of folders and documents. 
  - Its expected that only the top level documents are shown when the page first loads.
  - When you click on a folder, it should query the API for more data and update the view accordingly.

## Version 2

The next round of work will extend the base implementation to add the following features:

  - Have a search input that will show results (from all possible documents) to those that have its name or number match the search field
  - Have a button that will expand all the children, and another that will collapse all the children
  - Have a context menu pop up that shows the file size of the document when clicked

# Details

Details on building the base implementation:

  - Think of this as a green-fields/new build with freedom to choose whatever you feel is best.
  - Frameworks and libraries can be used.
  - The server response can be modified.
  - There are design mockups included in /designs to guide the look and feel.
  - We prefer responsive apps, vs building separate desktop and mobile apps.
  - Our browser support can be seen at https://dataroom.ansarada.com/_Login/BrowserSupport.asp

# Viewing the mock server

Reminder - you don't need to build the solution. But if you want to view the mock server, install NodeJS and then run (in the project folder):

```
npm install
node server/index.js
```
This will generate some dummy data to populate the api, as well as spin up a server at http://localhost:3000. Any files you put into the `client` folder will accessible.

API Definition:
```
/documents GET

  Gets a collection of documents.

  Params:
    parentId - int - Gets the children of a particular parent. By default, it returns the top level documents (parentId == null).
    search - string - Filters the query to documents that match the name and number or has a child that matches that name or number.
    includeChildren - 1 or 0. Includes the children of the found documents, filtered also by 'search'

  Returns:
    [
      {
        id : 4,
        parentId : 1,
        isFolder : false | true,
        name : "Name of the document",
        number : "Number of the document",
        fileSize : 1234556,
        children : [
          //List of this folder's children if includeChildren
        ]
      },
    ]
```
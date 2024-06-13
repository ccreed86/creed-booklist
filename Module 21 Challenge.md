# Module 21 Challenge

Most modern websites are driven by two things: data and user demands. This shouldn't come as a surprise, as the ability to personalize user data is the cornerstone of real-world web development today. And as user demands evolve, applications need to be more performant.

## MERN Challenge: Book Search Engine

This week, you'll take a fully functioning Google Books API search engine built with a RESTful API, and refactor it to be a GraphQL API built with Apollo Server. The app was built using the MERN stack, with a React front end, MongoDB database, and Node.js/Express.js server and API. It's already set up to allow users to save book searches to the back end.

To fulfill the Challenge, you’ll need to do the following:

1. Set up an Apollo Server to use GraphQL queries and mutations to fetch and modify data, replacing the existing RESTful API.

2. Modify the existing authentication middleware so that it works in the context of a GraphQL API.

3. Create an Apollo Provider so that requests can communicate with an Apollo Server.

4. Deploy the application to Render.

## IMPORTANT

Make sure to clone the starter code repository and make your own repository with the starter code. Do not fork the starter code repository!

Before you start, clone the starter code
https://github.com/coding-boot-camp/solid-broccoli

## User Story

    AS AN avid reader
    I WANT to search for new books to read
    SO THAT I can keep a list of books to purchase

## Acceptance Criteria

    GIVEN a book search engine
    WHEN I load the search engine
    THEN I am presented with a menu with the options Search for Books and Login/Signup and an input field to search for books and a submit button
    WHEN I click on the Search for Books menu option
    THEN I am presented with an input field to search for books and a submit button
    WHEN I am not logged in and enter a search term in the input field and click the submit button
    THEN I am presented with several search results, each featuring a book’s title, author, description, image, and a link to that book on the Google Books site
    WHEN I click on the Login/Signup menu option
    THEN a modal appears on the screen with a toggle between the option to log in or sign up
    WHEN the toggle is set to Signup
    THEN I am presented with three inputs for a username, an email address, and a password, and a signup button
    WHEN the toggle is set to Login
    THEN I am presented with two inputs for an email address and a password and login button
    WHEN I enter a valid email address and create a password and click on the signup button
    THEN my user account is created and I am logged in to the site
    WHEN I enter my account’s email address and password and click on the login button
    THEN I the modal closes and I am logged in to the site
    WHEN I am logged in to the site
    THEN the menu options change to Search for Books, an option to see my saved books, and Logout
    WHEN I am logged in and enter a search term in the input field and click the submit button
    THEN I am presented with several search results, each featuring a book’s title, author, description, image, and a link to that book on the Google Books site and a button to save a book to my account
    WHEN I click on the Save button on a book
    THEN that book’s information is saved to my account
    WHEN I click on the option to see my saved books
    THEN I am presented with all of the books I have saved to my account, each featuring the book’s title, author, description, image, and a link to that book on the Google Books site and a button to remove a book from my account
    WHEN I click on the Remove button on a book
    THEN that book is deleted from my saved books list
    WHEN I click on the Logout button
    THEN I am logged out of the site and presented with a menu with the options Search for Books and Login/Signup and an input field to search for books and a submit button  

## Getting Started

In order for this application to use a GraphQL API, you’ll need to refactor the API to use GraphQL on the back end and add some functionality to the front end. The following sections contain details about the files you’ll need to modify on the back end and the front end.

## IMPORTANT

Make sure to study the application before building upon it. Better yet, start by making a copy of it. It's already a working application—you're converting it from RESTful API practices to a GraphQL API.

### Back-End Specifications

* You’ll need to complete the following tasks in each of these back-end files:

*   auth.js: Update the auth middleware function to work with the GraphQL API.

*   server.js: Implement the Apollo Server and apply it to the Express server as middleware.

## Schemas directory:

* index.js: Export your typeDefs and resolvers.

* resolvers.js: Define the query and mutation functionality to work with the Mongoose models.

*HINT*

*Use the functionality in the user-controller.js as a guide.*

typeDefs.js: Define the necessary Query and Mutation types:

    Query type:

        me: Which returns a User type.

    Mutation type:

        login: Accepts an email and password as parameters; returns an Auth type.

        addUser: Accepts a username, email, and password as parameters; returns an Auth type.

        saveBook: Accepts a book author's array, description, title, bookId, image, and link as parameters; returns a User type. (Look into creating what's known as an input type to handle all of these parameters!)

        removeBook: Accepts a book's bookId as a parameter; returns a User type.

    User type:

        _id

        username

        email

        bookCount

        savedBooks (This will be an array of the Book type.)

    Book type:

        bookId (Not the _id, but the book's id value returned from Google's Book API.)

        authors (An array of strings, as there may be more than one author.)

        description

        title

        image

        link

    Auth type:

        token

        user (References the User type.)

## Front-End Specifications

You'll need to create the following front-end files:

* queries.js: This will hold the query GET_ME, which will execute the me query set up using Apollo Server.

    mutations.js:

        LOGIN_USER will execute the loginUser mutation set up using Apollo Server.

        ADD_USER will execute the addUser mutation.

        SAVE_BOOK will execute the saveBook mutation.

        REMOVE_BOOK will execute the removeBook mutation.

*Additionally, you’ll need to complete the following tasks in each of these front-end files:*

* App.jsx: Create an Apollo Provider to make every request work with the Apollo server.

* SearchBooks.jsx:

    * Use the Apollo useMutation() Hook to execute the SAVE_BOOK mutation in the handleSaveBook() function instead of the saveBook() function imported from the API file.

    * Make sure you keep the logic for saving the book's ID to state in the try...catch block!

    * SavedBooks.jsx:

    * Remove the useEffect() Hook that sets the state for UserData.

    * Instead, use the useQuery() Hook to execute the GET_ME query on load and save it to a variable named userData.

    * Use the useMutation() Hook to execute the REMOVE_BOOK mutation in the handleDeleteBook() function instead of the deleteBook() function that's imported from API file. (Make sure you keep the removeBookId() function in place!)

* SignupForm.jsx: Replace the addUser() functionality imported from the API file with the ADD_USER mutation functionality.

* LoginForm.jsx: Replace the loginUser() functionality imported from the API file with the LOGIN_USER mutation functionality.

## Grading Requirements

### NOTE
*If a Challenge assignment submission is marked as “0”, it is considered incomplete and will not count towards your graduation requirements. Examples of incomplete submissions include the following:*

* A repository that has no code

* A repository that includes a unique name but nothing else

* A repository that includes only a README file but nothing else

* A repository that only includes starter code

* This Challenge is graded based on the following criteria:

## Technical Acceptance Criteria: 40%

* Satisfies all of the preceding acceptance criteria plus the following:

* Has an Apollo Server that uses GraphQL queries and mutations to fetch and modify data, replacing the existing RESTful API.

* Use an Apollo Server and apply it to the Express.js server as middleware.

* Include schema settings for resolvers and typeDefs as outlined in the Challenge instructions.

* Modify the existing authentication middleware to work in the context of a GraphQL API.

* Use an Apollo Provider so that the application can communicate with the Apollo Server.

* Application must be deployed to Render.

## Deployment: 32%

* Application deployed at live URL.

* Application loads with no errors.

* Application GitHub URL submitted.

* GitHub repository contains application code.

## Application Quality: 15%

* User experience is intuitive and easy to navigate.

* User interface style is clean and polished.

* Application resembles the mock-up functionality provided in the Challenge instructions.

## Repository Quality: 13%

* Repository has a unique name.

* Repository follows best practices for file structure and naming conventions.

* Repository follows best practices for class/id naming conventions, indentation, quality comments, etc.

* Repository contains multiple descriptive commit messages.

* Repository contains a high-quality README file with description, screenshot, and link to the deployed application.

# How to Submit the Challenge

* You are required to submit BOTH of the following for review:

* The URL of the functional, deployed application.

* The URL of the GitHub repository. Give the repository a unique name and include a README describing the project.

### NOTE

*You are allowed to miss up to two Challenge assignments and still earn your certificate. If you complete all Challenge assignments, your lowest two grades will be dropped. If you wish to skip this assignment, click Next, and move on to the next Module.*

*Comments are disabled for graded submissions in BootCamp Spot. If you have questions about your feedback, please notify your instructional staff or the Student Success Advisor. If you would like to resubmit your work for an improved grade, you can use the Resubmit Assignment button to upload new links. You may resubmit up to three times for a total of four submissions.*

## IMPORTANT

It is your responsibility to include a note in the README section of your repo specifying code source and its location within your repo. This applies if you have worked with a peer on an assignment, used code in which you did not author or create sourced from a forum such as Stack Overflow, or you received code outside curriculum content from support staff such as an Instructor, TA, Tutor, or Learning Assistant. This will provide visibility to grading staff of your circumstance in order to avoid flagging your work as plagiarized.
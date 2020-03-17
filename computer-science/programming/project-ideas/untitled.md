# Untitled

[Sign in](https://medium.com/m/signin?operation=login&redirect=https%3A%2F%2Fblog.bitsrc.io%2F15-app-ideas-to-build-and-level-up-your-coding-skills-28612c72a3b1&source=post_page-----28612c72a3b1---------------------nav_reg-)[Get started](https://medium.com/m/signin?operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2F15-app-ideas-to-build-and-level-up-your-coding-skills-28612c72a3b1&source=post_page-----28612c72a3b1---------------------nav_reg-)[![Bits and Pieces](https://miro.medium.com/max/308/1*25Akp0ID7g7KRyM9jTC7rw.png)](https://blog.bitsrc.io/?source=post_page-----28612c72a3b1----------------------)

* [WRITE ✏️](https://blog.bitsrc.io/how-to-write-a-post-for-bits-and-pieces-13de0133151b?source=post_page-----28612c72a3b1----------------------)
* [BIT BLOG 🌎](https://blog.bitsrc.io/tagged/bit?source=post_page-----28612c72a3b1----------------------)
* [JAVASCRIPT ](https://blog.bitsrc.io/tagged/javascript?source=post_page-----28612c72a3b1----------------------)
* [WEBDEV](https://blog.bitsrc.io/tagged/web-development?source=post_page-----28612c72a3b1----------------------)
* [REACT](https://blog.bitsrc.io/tagged/react?source=post_page-----28612c72a3b1----------------------)
* [ANGULAR](https://blog.bitsrc.io/tagged/angular?source=post_page-----28612c72a3b1----------------------)
* [VUE](https://blog.bitsrc.io/tagged/vuejs?source=post_page-----28612c72a3b1----------------------)
* [⚡️ BUILD A COMPONENT LIBRARY →](https://bit.dev/?source=post_page-----28612c72a3b1----------------------)

**Top highlight**

## 15 App Ideas to Build and Level Up your Coding Skills

### App ideas that are great to improve your coding skills, experiment with new technologies and add to your portfolio!

[![Florin Pop](https://miro.medium.com/fit/c/96/96/1*6yPj-9aMYxi0Xnk5XNa0Lg.jpeg)](https://blog.bitsrc.io/@popflorin1705?source=post_page-----28612c72a3b1----------------------)[Florin Pop](https://blog.bitsrc.io/@popflorin1705?source=post_page-----28612c72a3b1----------------------)[Follow](https://medium.com/m/signin?operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2F15-app-ideas-to-build-and-level-up-your-coding-skills-28612c72a3b1&source=-d5b5242a7176-------------------------follow_byline-)[May 21, 2019](https://blog.bitsrc.io/15-app-ideas-to-build-and-level-up-your-coding-skills-28612c72a3b1?source=post_page-----28612c72a3b1----------------------) · 18 min read![](https://miro.medium.com/max/60/1*FRFBpWtkjXrhPrS148P7mg.png?q=20)![](https://miro.medium.com/max/2560/1*FRFBpWtkjXrhPrS148P7mg.png)

We all know that it can be hard sometimes to find new application ideas that you could build in order to either improve or learn a new programming language or framework.

**Tip**: When writing reusable code, turn into [**Bit components**](https://blog.bitsrc.io/bit.dev). Then you can easily share and reuse it across all your apps and projects, to easily build better modular software applications faster. It’s [open source](https://github.com/teambit/bit), give it a try.[Share reusable code components as a team · BitEasily share reusable components between projects and applications to build faster as a team. Collaborate to develop…bit.dev](https://bit.dev/)

In this article we’re going to look into 15 app ideas which are:

* great to improve your coding skills 💪;
* great to experiment with new technologies 🆕;
* great to be added in your portfolio to impress your next employer/client 📁;
* great to be used as examples in tutorials \(articles or videos\) 📃;
* easy to complete and also easily extendable with new features 👌;

And on top of that, each app idea has:

1. A clear and descriptive objective;
2. A list of _User Stories_ which should be implemented;
3. A list of _bonus features_ which are option, but “good-to-have”;
4. All the resources and links to help you find what you need to complete the project

We divided these app ideas into **three tiers** based on the knowledge and experience required to complete them. The tiers are: **Beginner**, **Intermediate** and **Advanced**.

In this article you’ll find 5 ideas from each tier.

## 1. Countdown Timer <a id="c255"></a>

Tier: 1-Beginner

We all have important events we look forward to in life, birthdays, anniversaries, and holidays to name a few. Wouldn’t it be nice to have an app that counts down the months, days, hours, minutes, and seconds to an event? Countdown Timer is just that app!

The objective of Countdown Timer is to provide a continuously decrementing display of the he months, days, hours, minutes, and seconds to a user entered event.

### Constraints <a id="b46b"></a>

* Use only builtin language functions for your calculations rather than relying on a library or package like [MomentJS](https://momentjs.com/). This assumes, of course, that the language of your choice has adequate date and time manipulation functions built in.
* You may not use any code generators such as the [Counting Down To](https://countingdownto.com/) site. You should develop your own original implementation.

### User Stories <a id="c06b"></a>

* User can see an event input box containing an event name field, an date field, an optional time, and a ‘Start’ button.
* User can define the event by entering its name, the date it is scheduled to take place, and an optional time of the event. If the time is omitted it is assumed to be at Midnight on the event date in the local time zone.
* User can see a warning message if the event name is blank.
* User can see a warning message if the event date or time are incorrectly entered.
* User can see a warning message if the time until the event data and time that has been entered would overflow the precision of the countdown timer.
* User can click on the ‘Start’ button to see the countdown timer start displaying the days, hours, minutes, and seconds until the event takes place.
* User can see the elements in the countdown timer automatically decrement. For example, when the remaining seconds count reaches 0 the remaining minutes count will decrement by 1 and the seconds will start to countdown from 59. This progression must take place from seconds all the way up to the remaining days position in countdown display.

### Bonus features <a id="bf13"></a>

* User can save the event so that it persists across sessions
* User can see an alert when the event is reached
* User can specify more than one event.
* User can see a countdown timers for each event that has been defined.

### Useful links and resources <a id="ebad"></a>

* Images of analog tube-based countdown timers can be found [here](https://nixieshop.com/)
* [`clearInterval`](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/clearInterval)[ MDN](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/clearInterval)
* [`setInterval`](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval)[ MDN](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval)
* [Date MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)

### Example projects <a id="bf73"></a>

[Countdown Timer built with React](https://www.florin-pop.com/blog/2019/05/countdown-built-with-react/)

[Simple Clock/Countdown Timer](https://codepen.io/karlo-stekovic/pen/OajKVK)

## 2. FlipImage <a id="bf2d"></a>

Tier: 1-Beginner

It’s important for Web Developers to understand the basics of manipulating images since rich web applications rely on images to add value to the user interface and user experience \(UI/UX\).

FlipImage explores one aspect of image manipulation — image rotation. This app displays a square pane containing a single image presented in a 2x2 matrix. Using a set of up, down, left, and right arrows adjacent to each of the images the user may flip them vertically or horizontally.

You must only use native HTML, CSS, and Javascript to implement this app. Image packages and libraries are not allowed.

### User Stories <a id="519f"></a>

* User can see a pane containing a single image repeated in a 2x2 matrix
* User can flip any one of the images vertically or horizontally using a set of up, down, left, and right arrows next to the image

### Bonus features <a id="755a"></a>

* User can change the default image by entering the URL of a different image in an input field
* User can display the new image by clicking a ‘Display’ button next to the input field
* User can see an error message if the new images URL is not found

### Useful links and resources <a id="54aa"></a>

* [How to Flip an Image](https://www.w3schools.com/howto/howto_css_flip_image.asp)
* [Create a CSS Flipping Animatin](https://davidwalsh.name/css-flip)

### Example projects <a id="fd64"></a>

[Image Effects by bennettfeely](https://codepen.io/seyedi/pen/gvqYQv)

## 3. Notes App <a id="bf7a"></a>

Tier: 1-Beginner

Create and store your notes for later purpose!

### User Stories <a id="ca4b"></a>

* User can create a note
* User can edit a note
* User can delete a note
* When closing the browser window the notes will be stored and when the User returns, the data will be retrieved

### Bonus features <a id="7432"></a>

* User can create and edit a note in Markdown format. On save it will convert Markdown to HTML
* User can see the date when he created the note

### Useful links and resources <a id="a846"></a>

* [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
* [Markdown Guide](https://www.markdownguide.org/basic-syntax/)
* [Marked — A markdown parser](https://github.com/markedjs/marked)

### Example projects <a id="c04b"></a>

[Markdown Notes built with Angular on Codepen](https://codepen.io/nickmoreton/full/gbyygq)

[Markdown Notes built with React](https://github.com/email2vimalraj/notes-app)

[Markdown Notes built with Angular 7 and bootstrap 4](https://github.com/omdnaik/angular-ui)

## 4. Recipe <a id="7920"></a>

Tier: 1-Beginner

You might not have realized this, but recipe’s are nothing more than culinary algorithms. Like programs, recipe’s are a series of imperative steps which, if followed correctly, result in a tasty dish.

The objective of the Recipe app is to help the user manage recipes in a way that will make them easy to follow.

### Constraints <a id="f45a"></a>

* For the initial version of this app the recipe data may be encoded as a JSON file. After implementing the initial version of this app you may expand on this to maintain recipes in a file or database.

### User Stories <a id="588d"></a>

* User can see a list of recipe titles
* User can click a recipe title to display a recipe card containing the recipe title, meal type \(breakfast, lunch, supper, or snack\), number of people it serves, its difficulty level \(beginner, intermediate, advanced\), the list of ingredients \(including their amounts\), and the preparation steps.
* User click a new recipe title to replace the current card with a new recipe.

### Bonus features <a id="9d64"></a>

* User can see a photo showing what the item looks like after it has been prepared.
* User can search for a recipe not in the list of recipe titles by entering the meal name into a search box and clicking a ‘Search’ button. Any open source recipe API may be used as the source for recipes \(see The MealDB below\).
* User can see a list of recipes matching the search terms
* User can click the name of the recipe to display its recipe card.
* User can see a warning message if no matching recipe was found.
* User can click a ‘Save’ button on the cards for recipes located through the API to save a copy to this apps recipe file or database.

### Useful links and resources <a id="a032"></a>

* [Using Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
* [Axios](https://www.npmjs.com/package/axios)
* [The MealDB API](https://www.themealdb.com/api.php)

### Example projects <a id="824a"></a>

[Recipe Box — a Free Code Camp Project \(FCC\)](https://codepen.io/eddyerburgh/pen/xVeJvB)

[React Recipe Box](https://codepen.io/inkblotty/pen/oxWRme)

## 5. Quiz App <a id="8db3"></a>

Tier: 1-Beginner

Practice and test your knowledge by answering questions in a quiz application.

As a developer you can create a quiz application for testing coding skills of other developers. \(HTML, CSS, JavaScript, Python, PHP, etc…\)

### User Stories <a id="c7b9"></a>

* User can start the quiz by pressing a `button`
* User can see a question with 4 possible answers
* After selecting an answer, display the next question to the User. Do this until the quiz is finished
* At the end, the User can see the following statistics
* Time it took to finish the quiz
* How many correct answers did he get
* A message showing if he `passed` or `failed` the quiz

### Bonus features <a id="1c31"></a>

* User can share the result of a quiz on social media
* Add multiple quizzes to the application. User can select which one to take
* User can create an account and have all the scores saved in his dashboard. User can complete a quiz multiple times

### Useful links and resources <a id="9f79"></a>

* [Open Trivia Database](https://opentdb.com/api_config.php)

### Example projects <a id="6609"></a>

[Quiz app built with React](http://tranquil-beyond-43849.herokuapp.com/) \(wait for it to load as it is hosted on Heroku\)

[Quiz app interface](https://codepen.io/FlorinPop17/full/qqYNgW)

## 6. Book Finder App <a id="def1"></a>

Tier: 2-Intermediate

Create an application that will allow users to search for books by entering a query \(Title, Author, etc\). Display the resulting books in a list on the page with all the corresponding data.

### User Stories <a id="717e"></a>

* User can enter a search query into an `input` field
* User can submit the query. This will call an API that will return an array of books with the corresponding data \(Title, Author, Published Date, Picture, etc\)
* User can see the list of books appearing on the page

### Bonus features <a id="fc99"></a>

* For each item in the list add a link that will send the User to an external site which has more information about the book
* Implement a Responsive Design
* Add loading animations

### Useful links and resources <a id="4004"></a>

You can use the [Google Books API](https://developers.google.com/books/docs/overview)

### Example projects <a id="d282"></a>

[Book Finder](https://book-finder-by-deyl.netlify.com/)

## 7. Card-Memory-Game <a id="e1d0"></a>

Tier: 2-Intermediate

Card memory is a game where you have to click on a card to see what image is underneath it and try to find the matching image underneath the other cards.

### User Stories <a id="216f"></a>

* User can see a grid with n x n cards \(`n` is an integer\). All the cards are faced down initially \(`hidden` state\)
* User can click a button to start the game. When this button is clicked, a timer will start
* User can click on any card to unveil the image that is underneath it \(change it to `visible` state\). The image will be displayed until the user clicks on a 2nd card

When the User clicks on the 2nd card:

* If there is a match, the 2 cards will be eliminated from the game \(either hide/remove them or leave them in the `visible` state\)
* If there isn’t a match, the 2 cards will flip back to their original state \(`hidden` state\)
* When all the matches have been found, the User can see a dialog box showing a Congratulations message with a counter displaying the time it took to finish the game

### Bonus features <a id="81f2"></a>

* Use can choose between multiple levels of difficulty \(Easy, Medium, Hard\). Increased difficulty means: decreasing the time available to complete and/or increasing the number of cards
* User can see the game statistics \(nr. of times he won / he lost, best time for each level\)

### Useful links and resources <a id="da5d"></a>

* [Wikipedia](https://en.wikipedia.org/wiki/Concentration_%28game%29)

### Example projects <a id="a8a6"></a>

[Flip — card memory game](https://codepen.io/zerospree/full/bNWbvW)

[Memory Game](https://jdmedlock.github.io/memorygame/)

[SMB3 Memory Card Game](https://codepen.io/hexagoncircle/full/OXBJxV)

## 8. Drawing App <a id="9989"></a>

Tier: 2-Intermediate

Create digital artwork on a canvas on the web to share online and also export as images.

### User Stories <a id="2b06"></a>

* User can draw in a `canvas` using the mouse
* User can change the color
* User can change the size of the tool
* User can press a button to clear the `canvas`

### Bonus features <a id="58db"></a>

* User can save the artwork as an image \(`.png`, `.jpg`, etc format\)
* User can draw different shapes \(`rectangle`, `circle`, `star`, etc\)
* User can share the artwork on social media

### Useful links and resources <a id="33cb"></a>

* [Learn how to create a Drawing Application using p5js](https://www.florin-pop.com/blog/2019/04/drawing-app-built-with-p5js/)

### Example projects <a id="9f85"></a>

[Drawing App by Florin Pop](https://codepen.io/FlorinPop17/full/VNYyZQ)

[Drawing App by t0mm4rx](https://codepen.io/t0mm4rx/full/dLowvZ)

## 9. Simple Online Store <a id="1298"></a>

Tier: 2-Intermediate

The goal of the Simple Online Store is to give your users the capability of selecting a product to purchase, viewing purchase information, adding it to an online shopping cart, and finally, actually purchasing the products in the shopping cart.

### Constraints <a id="6009"></a>

* Starting out you may implement your product inventory as an array of JavaScript objects if you are developing in JavaScript. For other languages feel free to choose the in memory solution of your choice.

### User Stories <a id="0362"></a>

* User can click on a ‘View Products’ button on the Landing Page to display the Products Page.
* User can see a card on the Products Page for each Product showing the product thumbnail, name, price, a short description, and a ‘Select’ button.
* User can see a Product Details page displayed when the ‘Select’ button is clicked showing the same information from the product card, but also a unique product id, a long description, ‘Add to Cart’ button, and a ‘See More Products’ button.
* User can see a confirmation message when the product is added to the shopping cart.
* User can click on the ‘See More Products’ page to return to the Products Page.
* User can see a ‘Shopping Cart’ button on both the Landing Page or the Products Page. Hint: a top bar might be a good common location for this button.
* User can click on the ‘Shopping Cart’ button to display the Shopping Cart page containing the product id, name, price, and quantity ordered input box for each product previously added to the Shopping Cart.
* User can see a total purchase amount on the Shopping Card that is calculated as the sum of the quantities multiplied by the unit price for each product ordered.
* User can adjust the quantity ordered for any product to adjust the total purchase amount.
* User can click a ‘Place Order’ button on the Shopping Cart Page to complete the order. User will see a confirmation number when the order has been placed.
* \[ \) User can click a ‘Cancel Order’ button on the Shopping Cart Page to cancel the order. User will see the product quantities and the total purchase amount reset to zero.
* User can click a ‘See More Products’ button on the Shopping Cart Page to return to the Products Page. If the order hasn’t been placed yet this will not clear the products that have already been added to the Products Page.

### Bonus features <a id="5234"></a>

* User can see an error message if the quantity ordered exceeds the “on hand” quantity of the product.
* User can specify a bill to and ship to address when the order is placed from the Shopping Cart Page
* User can see shipping charges added to the total purchase amount
* User can see sales taxes added to the total purchase amount
* Developer will implement the product inventory in an external file or a database.

### Useful links and resources <a id="06df"></a>

There are plenty of eCommerce Site Pages out there. You can use [Dribbble](https://github.com/florinpop17/app-ideas/blob/master/Projects/www.dribbble.com)and [Behance](https://github.com/florinpop17/app-ideas/blob/master/Projects/www.behance.net) for inspiration.

### Example projects <a id="af9e"></a>

[eCommerce Animations](https://codepen.io/RSH87/pen/RagqEv)

## 10. To-Do App <a id="13a2"></a>

Tier: 2-Intermediate

The classic To-Do application where a user can write down all the things he wants to accomplish.

### User Stories <a id="689c"></a>

* User can see an `input` field where he can type in a to-do item
* By pressing enter \(or a button\), the User can submit the to-do item and can see that being added to a list of to-do’s
* User can mark a to-do as `completed`
* User can remove a to-do item by pressing on a button \(or on the to-do item itself\)

### Bonus features <a id="2f3c"></a>

* User can edit a to-do
* User can see a list with all the completed to-do’s
* User can see a list with all the active to-do’s
* User can see the date when he created the to-do
* When closing the browser window the to-do’s will be stored and when the User returns, the data will be retrieved

### Useful links and resources <a id="4b8e"></a>

* [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)

### Example projects <a id="b220"></a>

[Todo App built with React](http://todomvc.com/examples/react/#/)

[To Do List on Codepen](https://codepen.io/yesilfasulye/pen/eJIuF)

## 11. Calorie Counter <a id="246e"></a>

Tier: 3-Advanced

Getting and staying healthy requires a combination of mental balance, exercise, and nutrition. The goal of the Calorie Counter app is to help the user address nutritional needs by counting calories for various foods.

This app provides the number of calories based on the result of a user search for a type of food. The U.S. Department of Agriculture MyPyramid Food Raw Data will be searched to determine the calorie values.

Calorie Counter also provides you, the developer, with experience in transforming raw data into a format that will make it easier to search. In this case, the MyPyramid Food Raw Data file, which is an MS Excel spreadsheet, must be downloaded and transformed into a JSON file that will be easier to load and search at runtime \(hint: take a look at the CSV file format\).

### User Stories <a id="9945"></a>

* Developer will create a JSON file containing the food items to be searched. This will be loaded when the app is started.
* User can see an panel containing a food description input text box, a ‘Search’ button, and a ‘Clear’ button.
* User can enter search terms into the food description input text box.
* User can click on the ‘Search’ button to search for the matching food.
* User can see and warning message if no search terms were entered.
* User can see a warning message if no matches were found.
* User can see a list of the matching food items, portion sizes, and calories in a scrollable results panel that is limited to 25 entries.
* User can click on the ‘Clear’ button to clear the search terms and results list.

### Bonus features <a id="3ed9"></a>

* User can see the count of the number of matching food items adjacent to the results list.
* User can use a wildcard character in search terms.
* User can see more than 25 entries from a search by clicking a Down icon button to add more matching food items to the search results list.
* Developer will implement load the MyPyramid data into a database or a data structure other than an array for faster searching.

### Useful links and resources <a id="96d1"></a>

[MyPyramid Food Raw Data](https://catalog.data.gov/dataset/mypyramid-food-raw-data-f9ed6)

### Example projects <a id="5fcb"></a>

[Food Calculator](https://www.webmd.com/diet/healthtool-food-calorie-counter)

## 12. Chat App <a id="c6d9"></a>

Tier: 3-Advanced

Real-time chat interface where multiple users can interact with each other by sending messages.

As a MVP\(Minimum Viable Product\) you can focus on building the Chat interface. Real-time functionality can be added later \(the bonus features\).

### User Stories <a id="da7c"></a>

* User is prompted to enter a username when he visits the chat app. The username will be stored in the application
* User can see an `input field` where he can type a new message
* By pressing the `enter` key or by clicking on the `send` button the text will be displayed in the `chat box` alongside his username \(e.g. `John Doe: Hello World!`\)

### Bonus features <a id="ddc8"></a>

* The messages will be visible to all the Users that are in the chat app \(using WebSockets\)
* When a new User joins the chat, a message is displayed to all the existing Users
* Messages are saved in a database
* User can send images, videos and links which will be displayed properly
* User can select and send an emoji
* Users can chat in private
* Users can join `channels` on specific topics

### Useful links and resources <a id="e562"></a>

* [Socket.io](https://socket.io/)
* [How to build a React.js chat app in 10 minutes — article](https://medium.freecodecamp.org/how-to-build-a-react-js-chat-app-in-10-minutes-c9233794642b)
* [Build a chat application like Slack — React / JavaScript Tutorial — Youtube](https://www.youtube.com/watch?v=a-JKj7m2LIo)
* [Socket.io Chat App Using Websockets — Youtube Tutorial](https://www.youtube.com/watch?v=tHbCkikFfDE)

### Example projects <a id="47e2"></a>

[Chatty2](https://web-chatty.herokuapp.com/)

## 13. GitHub Timeline <a id="9c40"></a>

Tier: 3-Advanced

API’s and graphical representation of information are hallmarks of modern web applications. GitHub Timeline combines the two to create a visual history of a users GitHub activity.

The goal of GitHub Timeline is accept a GitHub user name and produce a timeline containing each repo and annotated with the repo names, the date they were created, and their descriptions. The timeline should be one that could be shared with a prospective employer. It should be easy to read and make effective use of color and typography.

Only public GitHub repos should be displayed.

### User Stories <a id="7182"></a>

* User can enter a GitHub user name
* User can click a ‘Generate’ button to create and display the named users repo timeline
* User can see a warning message if the GitHub user name is not a valid GitHub user name.

### Bonus features <a id="6a8a"></a>

* User can see a summary of the number of repos tallied by the year they were created

### Useful links and resources <a id="8341"></a>

GitHub offers two API’s you may use to access repo data. You may also choose to use an NPM package to access the GitHub API.

Documentation for the GitHub API can be found at:

* [GitHub REST API V3](https://developer.github.com/v3/)
* [GitHub GraphQL API V4](https://developer.github.com/v4/)

Sample code showing how to use the GitHub API’s are:

* [GitHub REST API client for JavaScript](https://github.com/octokit/rest.js/)
* [GitHub GraphQL API client for browsers and Node](https://github.com/octokit/graphql.js)

You can use this CURL command to see the JSON returned by the V3 REST API for your repos:

```text
curl -u "user-id" https://api.github.com/users/user-id/repos
```

### Example projects <a id="7bb3"></a>

[CSS Timeline](https://codepen.io/NilsWe/pen/FemfK)

[Building a Vertical Timeline With CSS and a Touch of JavaScript](https://codepen.io/tutsplus/pen/QNeJgR)

## 14. Shuffle Card Deck <a id="da52"></a>

Tier: 3-Advanced

As a Web Developer you’ll be asked to come up with innovative applications that solve real world problems for real people. But something you’ll quickly learn is that no matter how many wonderful features you pack into an app users won’t use it if it isn’t performant. In other words, there is a direct link between how an app performs and whether users perceive it as usable.

The objective of the Shuffle Card Deck app is to find the fastest technique for shuffling a deck of cards you can use in game apps you create. But, more important it will provide you with experience at measuring and evaluating app performance.

Your task is to implement the performance evaluation algorithm, the Xorshift pseudorandom number generator, as well as the WELL512a.c algorithm if you choose to attempt the bonus feature.

### User Stories <a id="a03b"></a>

* User can see a panel containing a text box the user can enter the number of rounds into, three output text boxes to contain the starting time, ending time, and total time of the test, and two buttons — ‘JS Random’, ‘Xorshift’.
* User can enter a number from 1 to 10,000 to specify the number of times \(or rounds\) the selected random number is to be executed.
* User can click one of the three buttons to start the evaluation of the selected random number algorithm. The random number algorithm will be executed for the number of rounds entered by the user above.
* User can see a warning message if number of rounds has not been entered, if it is not within the range 1 to 10,000, or if it is not a valid integer.
* User can see a tabular output area where the results of each algorithm are displayed — algorithm name, time started, time ended, and total time.
* User can see a warning dialog with a ‘Cancel’ and a ‘OK’ button if the number of rounds is changed before all three tests have been run.
* User can click the ‘Cancel’ button in the warning dialog to dismiss the dialog with no changes.
* User can click the ‘OK’ button in the warning dialog to clear the output area and close the warning dialog.

### Bonus features <a id="e4df"></a>

* User can see a third algorithm button — ‘WELL512a.c’.
* Developer should review the output and determine why the fastest algorithm is faster than the slowest algorithm.

### Useful links and resources <a id="a6cc"></a>

* [Random Number Generation \(Wikipedia\)](https://en.wikipedia.org/wiki/Random_number_generation)
* [Math.random \(MDN\)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)
* [Xorshift \(Wikipedia\)](https://en.wikipedia.org/wiki/Xorshift)
* [WELL512a.c](http://www.iro.umontreal.ca/~panneton/well/WELL512a.c)
* [console.time \(MDN\)](https://developer.mozilla.org/en-US/docs/Web/API/Console/time)
* [Using the Chrome DevTools Audit Feature to Measure and Optimize Performance \(Part 1\)](https://medium.com/chingu/using-the-chrome-devtools-audit-feature-to-measure-and-optimize-performance-part-1-868a20bbfde8)
* [Using the Chrome DevTools Audit Feature to Measure and Optimize Performance \(Part 2\)](https://medium.com/chingu/using-the-chrome-devtools-audit-feature-to-measure-and-optimize-performance-part-2-af4a78bc6cf0)

## 15. Survey App <a id="c6a6"></a>

Tier: 3-Advanced

Surveys are a valuable part of any developers toolbox. They are useful for getting feedback from your users on a variety of topics including application satisfaction, requirements, upcoming needs, issues, priorities, and just plain aggravations to name a few.

The Survey app gives you the opportunity to learn by developing a full-featured app that you can add to your toolbox. It provides the ability to define a survey, allow users to respond within a predefined timeframe, and tabulate and present results.

Users of this app are divided into two distinct roles, each having different requirements:

* _Survey Coordinators_ define and conduct surveys. This is an administrative function not available to normal users.
* _Survey Respondents_ Complete surveys and view results. They have no administrative privileges within the app.

Commercial survey tools include distribution functionality that mass emails surveys to Survey Respondents. For simplicity, this app assumes that surveys open for responses will be accessed from the app’s web page.

### User Stories — General <a id="5e90"></a>

* Survey Coordinators and Survey Respondents can define, conduct, and view surveys and survey results from a common website
* Survey Coordinators can login to the app to access administrative functions, like defining a survey.

### Defining a Survey <a id="45af"></a>

* Survey Coordinator can define a survey containing 1–10 multiple choice questions.
* Survey Coordinator can define 1–5 mutually exclusive selections to each question.
* Survey Coordinator can enter a title for the survey.
* Survey Coordinator can click a ‘Cancel’ button to return to the home page without saving the survey.
* Survey Coordinator can click a ‘Save’ button save a survey.

### Conducting a Survey <a id="6727"></a>

* Survey Coordinator can open a survey by selecting a survey from a list of previously defined surveys
* Survey Coordinators can close a survey by selecting it from a list of open surveys
* Survey Respondent can complete a survey by selecting it from a list of open surveys
* Survey Respondent can select responses to survey questions by clicking on a checkbox
* Survey Respondents can see that a previously selected response will automatically be unchecked if a different response is clicked.
* Survey Respondents can click a ‘Cancel’ button to return to the home page without submitting the survey.
* Survey Respondents can click a ‘Submit’ button submit their responses to the survey.
* Survey Respondents can see an error message if ‘Submit’ is clicked, but not all questions have been responded to.

### Viewing Survey Results <a id="51f0"></a>

* Survey Coordinators and Survey Respondents can select the survey to display from a list of closed surveys
* Survey Coordinators and Survey Respondents can view survey results as in tabular format showing the number of responses for each of the possible selections to the questions.

### Bonus features <a id="11a9"></a>

* Survey Respondents can create a unique account in the app
* Survey Respondents can login to the app
* Survey Respondents cannot complete the same survey more than once
* Survey Coordinators and Survey Respondents can view graphical representations of survey results \(e.g. pie, bar, column, etc. charts\)

### Useful links and resources <a id="d275"></a>

Libraries for building surveys:

* [SurveyJS](https://surveyjs.io/Overview/Library/)

Some commercial survey services include:

* [Survey Monkey](https://www.surveymonkey.com/)
* [Traversy](https://youtu.be/SSDED3XKz-0)
* [Typeform](https://www.typeform.com/)

### Example projects <a id="1fec"></a>

[Javascript Questionnaire](https://codepen.io/amyfu/pen/oLChg)

## Conclusion <a id="9eef"></a>

Now you have a basis of 15 applications that you can play with. We created a [GitHub ](https://github.com/florinpop17/app-ideas)repository where you can find even more ideas if you are interested and you are welcomed to contribute, share and give it a star!

Happy Coding! ^\_^

## Learn More <a id="beb9"></a>

[10 VS Code Extensions for FrontEnd Developers in 201910 VS Code extensions to speed your web development.blog.bitsrc.io](https://blog.bitsrc.io/top-10-vs-code-extensions-for-frontend-developers-in-2018-7992282db2ca)[Building a UI Component Design SystemLearn how Uber, Pinterest, Shopify and Airbnb are leveraging components to build a consistent UI/UX design system.blog.bitsrc.io](https://blog.bitsrc.io/building-a-consistent-ui-design-system-4481fb37470f)[9 React Libraries and Tools to Master your Component Workflow9 React UI component libraries and tools to speed your workflow.blog.bitsrc.io](https://blog.bitsrc.io/9-tools-and-libraries-to-boost-your-react-component-workflow-6ff4b49511c2)[Share reusable code components as a team · BitEasily share reusable components between projects and applications to build faster as a team. Collaborate to develop…bit.dev](https://bit.dev/)[Bits and Pieces](https://blog.bitsrc.io/?source=post_sidebar--------------------------post_sidebar-)

**Th best of frontend development articles, tutorials, and news.**

[Follow](https://medium.com/m/signin?operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2F15-app-ideas-to-build-and-level-up-your-coding-skills-28612c72a3b1&source=post_sidebar--------------------------follow_sidebar-)

**2.6K**

* [Application](https://blog.bitsrc.io/tag/application)
* [Programming](https://blog.bitsrc.io/tag/programming)
* [JavaScript](https://blog.bitsrc.io/tag/javascript)
* [Web Development](https://blog.bitsrc.io/tag/web-development)
* [Web Design](https://blog.bitsrc.io/tag/web-design)

**2.6K claps**

[![Florin Pop](https://miro.medium.com/fit/c/160/160/1*6yPj-9aMYxi0Xnk5XNa0Lg.jpeg)](https://blog.bitsrc.io/@popflorin1705?source=follow_footer--------------------------follow_footer-)

WRITTEN BY

### [Florin Pop](https://blog.bitsrc.io/@popflorin1705?source=follow_footer--------------------------follow_footer-)

[Follow](https://medium.com/m/signin?operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2F15-app-ideas-to-build-and-level-up-your-coding-skills-28612c72a3b1&source=follow_footer-d5b5242a7176-------------------------follow_footer-)

**JavaScript enthusiast 🙌, Front-end developer 💻 & Blogger at https://florin-pop.com/blog/**

[![Bits and Pieces](https://miro.medium.com/fit/c/160/160/1*ds6iXWSFwycgEjbhZiCB4A.png)](https://blog.bitsrc.io/?source=follow_footer--------------------------follow_footer-)

### [Bits and Pieces](https://blog.bitsrc.io/?source=follow_footer--------------------------follow_footer-)

[Follow](https://medium.com/m/signin?operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2F15-app-ideas-to-build-and-level-up-your-coding-skills-28612c72a3b1&source=follow_footer--------------------------follow_footer-)

**Th best of frontend development articles, tutorials, and news.**

[See responses \(5\)](https://medium.com/p/28612c72a3b1/responses/show?source=follow_footer--------------------------follow_footer-)

### More From Medium

**More from Bits and Pieces**

[3 Ways to Render Large Lists in Angular](https://blog.bitsrc.io/3-ways-to-render-large-lists-in-angular-9f4dcb9b65?source=post_recirc---------0------------------)[![Giancarlo Buomprisco](https://miro.medium.com/fit/c/80/80/1*e-SCPgqED_0q54vd1HN1xA.jpeg)](https://blog.bitsrc.io/@.gc?source=post_recirc---------0------------------)[Giancarlo Buomprisco](https://blog.bitsrc.io/@.gc?source=post_recirc---------0------------------) in [Bits and Pieces](https://blog.bitsrc.io/?source=post_recirc---------0------------------)[Mar 5](https://blog.bitsrc.io/3-ways-to-render-large-lists-in-angular-9f4dcb9b65?source=post_recirc---------0------------------) · 7 min read

**927** 

**More from Bits and Pieces**

[React TypeScript: Basics and Best Practices](https://blog.bitsrc.io/react-typescript-cheetsheet-2b6fa2cecfe2?source=post_recirc---------1------------------)[![Fernando Doglio](https://miro.medium.com/fit/c/80/80/1*w12_5tQWwj3V1nS8wOc3Hg.jpeg)](https://blog.bitsrc.io/@deleteman123?source=post_recirc---------1------------------)[Fernando Doglio](https://blog.bitsrc.io/@deleteman123?source=post_recirc---------1------------------) in [Bits and Pieces](https://blog.bitsrc.io/?source=post_recirc---------1------------------)[Mar 3](https://blog.bitsrc.io/react-typescript-cheetsheet-2b6fa2cecfe2?source=post_recirc---------1------------------) · 7 min read

**701** 

**More from Bits and Pieces**

[An Opinionated Coding Styleguide for Angular](https://blog.bitsrc.io/an-opinionated-styleguide-for-angular-af623d54e2b8?source=post_recirc---------2------------------)[![Giancarlo Buomprisco](https://miro.medium.com/fit/c/80/80/1*e-SCPgqED_0q54vd1HN1xA.jpeg)](https://blog.bitsrc.io/@.gc?source=post_recirc---------2------------------)[Giancarlo Buomprisco](https://blog.bitsrc.io/@.gc?source=post_recirc---------2------------------) in [Bits and Pieces](https://blog.bitsrc.io/?source=post_recirc---------2------------------)[Mar 9](https://blog.bitsrc.io/an-opinionated-styleguide-for-angular-af623d54e2b8?source=post_recirc---------2------------------) · 9 min read

**785** 

[Discover Medium](https://medium.com/about?autoplay=1&source=post_page-----28612c72a3b1----------------------)Welcome to a place where words matter. On Medium, smart voices and original ideas take center stage - with no ads in sight. [Watch](https://medium.com/about?autoplay=1&source=post_page-----28612c72a3b1----------------------)[Make Medium yours](https://medium.com/topics?source=post_page-----28612c72a3b1----------------------)Follow all the topics you care about, and we’ll deliver the best stories for you to your homepage and inbox. [Explore](https://medium.com/topics?source=post_page-----28612c72a3b1----------------------)[Become a member](https://medium.com/membership?source=post_page-----28612c72a3b1----------------------)Get unlimited access to the best stories on Medium — and support writers while you’re at it. Just $5/month. [Upgrade](https://medium.com/membership?source=post_page-----28612c72a3b1----------------------)[About](https://medium.com/about?autoplay=1&source=post_page-----28612c72a3b1----------------------)[Help](https://help.medium.com/?source=post_page-----28612c72a3b1----------------------)[Legal](https://medium.com/policy/9db0094a1e0f?source=post_page-----28612c72a3b1----------------------)


# Final project - A personal blogging system - Team Try Catch Me

This was a team project I participated in during the first semester of my master's program. The project adopts a modern frontend-backend separation architecture, with the frontend built using Svelte and the backend developed with Node.js/Express and a SQL database. It integrates features such as real-time notifications, article management, user authentication, and interactive comments. 

This project demonstrates my practical experience in full-stack development, teamwork, and project management, and it was my very first team-based software development project.


My team members are:
- Musyafa Muhammad
- Aidil Muslim 
- Manu R 
- Yang Wu 

## Development Environment Setup & Commit Guidelines

Extensions to install:

- [VSCode Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [VSCode Svelete](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode)
- **Postman**

Commands to run before commits:

- In Backend `npm run format` to double check code is formatted
- In Frontend `npm run format` to double check code is formatted

All commits MUST have a brief descriptive message

## ✅ Questions / Information required from the Handout

> 1.Are there any special setup instructions, beyond initialising the database and running your project?

In our application, we implemented real-time notification system. To test this system, We have configured the backend server to accept HTTP request from port 5174.

To activate the second frontend, simply open two integrated terminals in the frontend project folder. and run `npm run dev` in both terminals.

The user will be notified only when there is another user likes their article, likes their comment, comments their article or replies their comments.

For best results, log in with two different user accounts in each frontend window. When one user interacts with another’s content (like, comment, reply), the recipient will see a notification pop up instantly in the notification dropdown—no page refresh required.

> 2.At least two usernames / passwords for existing users in your system with some already-published articles & comments

- User account username/password: **testuser / Test123!**
- User account security answer: **testuser_answer**
- Admin account username/password: **admin / Admin123!**
- Admin account security answer: **admin_answer**

> 3.API documentation

**(1) Endpoint address /api/articles**
- POST /api/articles - Create a new article (requires authentication). Supports image upload.
- POST /api/articles/upload-images - Upload images for articles (requires authentication).
- GET /api/articles - Get a list of articles. Supports search, sort, and filter by author.
- GET /api/articles/author/:authorId/count - Get the number of articles for a specific author.
- GET /api/articles/:articleId - Get a single article by ID, including its images.
- GET /api/articles/liked/:userId - Get articles liked by a user (requires authentication).
- PUT /api/articles/:articleId - Update an article (author or admin only).
- DELETE /api/articles/:articleId - Delete an article (author or admin only).

**(2) Endpoint address /api/articles/:articleId/comments**
- POST  /api/articles/:articleId/comments - Add a new comment or reply to an article (require authentication).
- GET /api/articles/:articleId/comments - Get all comments for an article.

**(3) Endpoint address /api/articles/:articleId/comments/:commentId**
- GET - Get a single comment by ID.
- PATCH - Update a comment (author only).
- DELETE - Delete a comment (author, article author, or admin only).


**(4) Endpoint address /api/articles/:articleId/likes**
- POST - Like an article (requires authentication).
- GET - Get all likes for an article.
- DELETE - Remove like from an article (requires authentication).

**(5) Endpoint address /api/articles/:articleId/images**
- GET - Get all images for an article

**(6) Endpoint address /api/comments**
- POST - Add a new comment (requires authentication).
- GET - Get all comments (admin or for moderation).

**(7) Endpoint address /api/auth**
- POST /api/auth/login - Log in a user.
- POST /api/auth/logout - Log out the current user.
- POST /api/auth/register - Register a new user.
- POST /api/auth/refresh - Refresh authentication token.

**(8) Endpoint address /api/users**
- POST - Register a new user.
- GET - Get all users (admin only).

**(9) Endpoint address /api/users/:id**
- GET - Get a user by ID.
- PATCH - Update user profile (self or admin).
- DELETE - Delete a user (self or admin)

**(10) Endpoint address /api/notifications**
- GET - Get notifications for the current user (requires authentication)
- PATCH /api/notifications/mark-all-read - Mark all notifications as read.

> 4.Description of all pages in your webapp

In our web application we have multiple pages that serve their functionality

**(1) Home page/Landing page - Show all articles in the application**

This is the primary entry point for both guests and logged-in users. The page displays a comprehensive list of all articles available in the application, as well as highlighting the top authors with the most likes and posts.

At the top of the page, the application header includes a search box and sorting features, enabling users to easily find and organize articles. In addition, a notification feature delivers real-time alerts when other users like, comment on, or reply to their articles or comments, ensuring users stay engaged and informed.

On the left side, there is a sidebar that enables users to quickly navigate to other pages such as the Favourites, About. The interface also supports both light and dark modes, allowing users to switch between them according to their preference.

For guests (not logged-in users), access is limited to browsing and viewing articles. To access advanced features, such as managing favourites, leaving comments or posting articles, they need to register for an account and log in.

**(2)Registration Page - Register/add new user account**

The Registration Page allows new users to create an account by submitting required personal information such as username, first name, last name, password, date of birth, and a short bio. During registration, users can either select an avatar from the available options or upload their own profile picture; if no avatar is chosen, a default image will be assigned automatically.

To ensure account security, the page includes a validation mechanism that checks for unique usernames and enforces strong password requirements. Additionally, users are required to set up a security question for the "forgot password" feature, which provides account recovery support.

**(3)Login Page - Authenticate user’s account and forgot password feature**

The Login Page provides authentication functionality, enabling users to securely access their accounts by entering their username and password. If users forget their password, they can follow on-screen instructions to retrieve and reset it using the "Forgot Password" feature.

A noteworthy feature is a light/dark mode button is also available on the login and register page.

**(4)Profile Page (login required) - Show account details and articles created by the account**

The Profile Page displays information about the logged-in user’s account, including the header picture (which is automatically set when the account is created and cannot be changed), profile photo, username, and other relevant details. All user profile information can be modified via the "Edit Profile" button.

Users can see a list of all articles they have created directly on their own profile page, while browsing other users’ profiles with articles. Users can also edit or delete each of their articles directly from their profile. Edit and delete actions are accessible through buttons located at the top right corner of each article.

A statistics board on the profile page allows users to see data of their own engagement, including the total number of posts, total likes received, and their post with the highest number of likes. 

A prominent plus (“+”) button is consistently available, allowing users to quickly compose and publish a new article, complete with a header image, multiple images, and content. In addition, an auto-revealed arrow button, located near the post article (“+”) button, allows users to instantly return to the top of the page after scrolling, enhancing navigation and overall user experience. Both the post article button and quick-scroll button are available throughout the entire application.

**(5)About Page - Information about this web project and mini game**

Provides background information about the web application. A built-in mini game is also introduced in and themed to align with our team name and adds a unique, interactive element to the platform.

**(6)Article Page - Display a specific article**

When users click on an article title, they are directed to the Article Page, where they can view the full content of the selected article, including all related details. Users can read the article in detail, and view or leave comments on the article. This page basically enables open discussion and interaction under each article.

**(7)Favourites Page (login required) - Show all liked articles**

Displays a personalized list of articles that the user has liked.

**(8)Search Page - Show the search results**

Displays the results after users enter keywords or apply filters in the search box. Searches are performed specifically on the titles and content of the articles, ensuring that only articles containing the specified keywords in their title or body will appear in the results.

**(9)Settings Page (login required) - For changing password, changing username and delete account**

Provides account management features for logged-in users to change their username or password, or permanently delete their account. Security checks and confirmation steps are included to prevent accidental modifications.

**(10)Error Page - Only be displayed when users try to access an unavailable page, e.g. searching non-existent users.**


> 5.Description of how to use your Java Swing admin interface

Our Java Swing admin client can only be used by admin users. If a valid user who is not an admin tries to log in to the system. The user will be logged out with an error message.

Here is the procedure of how to user the Java Swing admin client

(1) Run your backend server.

(2) Run the Admin Client:

    a. If you are using the default API address (http://localhost:3000), simply run the main Java class.

    b. If your backend server is running on a different domain or address, run the main Java class from the command prompt and provide your backend server address as an argument.

(3) Log In with the username and password of a valid admin account.

(4) User Management:

    a. After logging in, you will be served by a table of all registered users from the web application database. 

    b. Select any user to see their profile picture. 
    
    c. You can also delete a user by clicking the desired user. After clicking the desired user, the delete button will be enabled. You can click that button to delete the account. 
    
    d. Note: You cannot delete the account you are currently logged in with.

(5) To log out, simply click the log out button.


> 6.Any other instructions / comments you wish to make to your markers
    
    a. We have already provided accounts to use but you may also register new different accounts

    b. Real-time notifications require two frontends running and logged in with different accounts to see the notification being pushed throughout frontends. though, you can test it by changing account in one window.

    c. Java Swing admin client requires backend running and an admin account.

    d. Try our mini game on the About page, it is simple but addicting :)

    e. We do hope your feedback and suggestion for our learning references in the future.


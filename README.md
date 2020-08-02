# Dibs

[Backend Repo](https://github.com/DawtDawt/dibs-backend)

[Frontend Repo](https://github.com/yehmond/dibs-frontend)

Dibs is an online barbershop-reservation service which supports barber service booking and barbershop information management.
Dibs enables both owners and customers to register on the platforms. Owners are able to advertise their shops, services, and individual barbers, as well as
visualize daily schedules and past booking statistics, while customers are able to book appointments and leave reviews for their 
favorite barbershops. Dibs is an all-in-one platform for barbershop customers and owners to manage their personal care needs.


## Goals Overview

##### 3-5 minimal requirements

-   Create two user roles: owner and customer  ✅
-   Allow users to create a reservation entry  ✅
-   Allow owners to create a barbershop/salon entry  ✅

##### 3-7 "standard" requirement

-   Show a list of customers to the barbershop owner  ✅
-   Show statistics about reservations to barbershop owners  ✅
-   Search a given barbershop  ✅
-   Delete a reservation  ✅
-   Prevent double bookings  ✅

##### 2-3 stretch requirements

-   A rating system for the barbershops/barbers that users can participate in  ✅
-   A map containing all of the barbershops available on the site ⚠
 - A schedule that displays the barbershop's availability with filters for individual barbers.  ✅

## Tech Overview

##### Unit 1 - HTML/CSS
SCSS variables were utilized to create a single point of control for the colour scheme of our application, enabling
different color palettes to be chosen simply by switching the values of a few variables. We also utilized React Material-UI to
render several native HTML components, such as buttons and inputs, in order to create a consistent look and feel across our
application.
##### Unit 2 - React/Redux
Modularized several re-usable components that were used across many screens/pages via React class and functional components. 
React hooks were used in place of lifecycle methods due to their ease of use and to enhance code readability. To ensure user information
was accessible across the component tree, we used React Context and the associated hooks so that each component did not need
to individually connect to the Redux state. Redux was used to manage authorization, as well as for the search functionality, including 
the filtering logic. As a design decision, we decided to keep the frontend as light as possible and make API calls when fetching barbershop
information. 
##### Unit 3 - MongoDB
MongoDB and NoSQL was used to persist our data. Although a Relational model would have likely been better suited to our application,
we were able to utilize MongoDB indexes to allow us to have separate collections while maintaining speed in our queries. Our collections 
consisted of: Users, Barbershops, Barbers, Reviews, and Reservations. 
##### Unit 4 - Backend/Express
In the backend, we used a series of middleware such as bcrypt, dotenv and JWT tokens to keep our information confidential and secure, 
Mongoose was used as a data model to enable seamless communication between the backend and the database. Body-parser with Express
allowed us to easily facilitate the connection between the frontend and the backend.
##### Unit 5 - Release Engineering
The app was deployed via Heroku, using a submodule structure. The backend and frontend were developed in separate repositories, with 
a parent repository using git submodules to connect the client and server in deployment. Heroku prebuild scripts allowed us to build 
the frontend statically and serve them via the backend server. Continuous deployment was enabled via Heroku pipelines, where
pushes to our master branch would trigger a new build. Environment variables were used to store secure information, such as JWT secret and 
API keys.

## Above and Beyond Functionality
Dibs goes above and beyond in several aspects. Firstly, the app is fully mobile responsive for both desktop and 
mobile views. This was achieved via CSS media queries and strategic use of SCSS inheritance to 
enable class selectors and ID selectors to worth together to change styling for mobile views.
Secondly, our app is integrated with different external APIs, including node Geocoder, where addresses are 
translate into lat/lon coordinates, where our Google Maps API is then able to render a mini-map.


In addition, our user authentication utilizes best practices, avoiding local storage to store tokens, but
instead using httpOnly cookies for maximum security. 
The backend algorithms are also optimized for returning multi-structural data from NoSQL MongoDB documents, and 
structured on asynchronous code (async/await and promises) whenever necessary to avoid race conditions.


Lastly, the depth of the Dibs application is a critical part of what sets it apart. The app is optimized to deliver a 
custom experience for both owners and customers, and offers a wide range of functionalities for both parties. Not only is
it a reservation system, it is also a management system for owners, offering scheduling visualization, statistics, and 
advertising. 

## Next Steps
In the next steps, our app is looking forward to supporting multiple languages for non-English users. In the meanwhile, we are also looking to integrate with social media, 
such as Facebook and Twitter, to allow users to log in with social media accounts and receive barbershop updates.

In addition, for a future release, we would like to implement clear error messaging for all potential errors,
enhance the statistics available to show barber owners, enhanced rating/recommendation system, as well as enable support for 
editing existing store/barber information.

## List of Contributions

##### Ray
- Implemented the authentication scheme on the frontend and the authentication endpoints on the backend.
- Added redirecting routes for authentication required pages on the frontend
- Created the Home and Browse page, as well as components such as the navbar, searchbar, cards, filters etc. 
- Configured eslint, prettier, and git branching strategies



##### Jeremy 
- Deployed project to heroku, set up parent repo with git submodules.
- Created the registration pages for barbershops and barbers
- Created the Barbershop Profile pages as well as Schedule View for owners,
and the statistics for owners. 
- Set Material UI Theme and SCSS in the project


##### TJ 
- Designed, developed, integrated, and tested the minimal, standard and stretch requirement for our backend and endpoints (including schemas, external packages, functions, etc).
- Populated the backend with fake data.
- Integrated external third party APIs for our backend (such as node-geocoder).
	

##### Yongxin
- Created frontend UI for reservation, reservation history, and reservation rating page. 
- Hooked up reservation page for getting barbershop information and sending booking requests.


#### Manual Deployment Instructions

To bring in all changes, run `git submodule update --remote`. 

Then, commit and push to the git repository via `git commit -am "message" && git push`.

To deploy run `git push heroku master`.
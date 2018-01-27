Restaurant App
======

Restaurant app is an application that let's a user come to webpage, search for restaurants by location, and pick favorite restaurants. 

1. A Home Page that displays a form for the user to search with
2. A result of that search page 
3. A page to see their favorites 

For this application you first off will need a Yelp developer API key that will give us access to their popular Fusion API. You will need to create a yelp account if you do not have one and then go to then create an app at the following URL.

[https://www.yelp.com/developers/v3/manage_app](https://www.yelp.com/developers/v3/manage_app)

Once you have create the app it is time to scaffold out your project 

Once you are in an empty folder run `npm init` to create your `package.json` and fill it the form as you see fit. 

Then you will need install the necessary packages for this project: 

run `npm install body-parser dotenv express express-handlebars mysql2 sequelize yelpv3` in your terminal

Then using the `sequelize-cli` run the command 

`sequelize init:config & sequelize init:models` to create your sequelize folders

You will need to make a local version of your database with the following script and update that information in the `config.json`.

```
DROP DATABASE IF EXISTS `restaurantDb`;
CREATE DATABASE `restaurantDb`;
USE `restaurantDb`;
```

You will only need one model for sequelize and you can call it `Favorite`, which will hold the `name`, `image_url`, and `page_url` for each favorite restaurant selected by the user. The `name` and `page_url` should be `DataTypes.STRING` and the `image_url` should be `DataTypes.TEXT` due to it possibly being a long URL.

What will be happening here is that when a user clicks on a favorite button, the name, image_url, and page_url will get sent the database with our favorites table in it. 

You will also need to create your handlebars folders and can follow the documentation for the `express-handlebars` found [here](https://www.npmjs.com/package/express-handlebars#basic-usage)

The `yelpv3` package is the one you are going to use to get results from the Yelp API. The NPM page for this can be found below. Keep in mind that the location paramter can take in a string like "San Diego" and come back with relevant restaurant data. 

You can find all the documentation here for it at t the following page 
[https://www.npmjs.com/package/yelpv3](https://www.npmjs.com/package/yelpv3)

When using the app you will need your yelp Client ID and Client Secret to initliaze the constructor for this package to run.

```
var Yelp = require('yelpv3');

var yelp = new Yelp({
    app_id: YOUR_YELP_CLIENT_ID,
    app_secret: YOUR_YELP_SECRET_KEY
});
```

After all this has been setup it is up to you to code the rest! If you need a demo you can find one here:

[https://restaurant-app-cbc.herokuapp.com/](https://restaurant-app-cbc.herokuapp.com/)

Good luck and have fun!

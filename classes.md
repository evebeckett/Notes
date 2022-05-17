## Why use a class?

If you want to create several different objects that follow the same format, use a class to do that instead of manually creating severeal different object literals.

## What is a class?

Classes in JS are like blue prints that describe a particular object in a non-specific way.

For example, a User class might have the following values:

- email
- name
- status
- login()
- logout()

Each object created would have these values, but the value for each might be different for each object.

## How do we create a class?

An empty user class looks like:

    class User {

    }

The first thing we need to do inside a class is create a *constructor function*.

## What is a constructor function?

A constructor function is the function that actually constructs/creates our object. It's inserted inside our class, like this:

    class User {
        constructor() {

        }
    }

At some point in our code later on, we can say:

    var userOne = new User()

### What is the "new" keyword doing?

- Creates a new empty object {}
- Sets the value of 'this' to be the new empty object
- calls the constructor method (function)

## Look at an example:

    class User {
        constructor (email, name) {
            this.email = email;
            this.name = name;
        }
    }

    var userOne = new User('ryu@ninjas.com', 'Ryu');

    var userTwo = new User('yoshi@mariokorp.com', 'Yoshi')

    console.log(userOne);
    console.log(userTwo);

This will give us two different objects with the same keys, but different values for those keys:

    User {
        email: 'ryu@ninjas.com', 
        name: 'ryu'
    }

    User {
        email: 'yoshi@mariokorp.com',
        name: 'Yoshi'
    }

## Creating Methods for Classes

You can associate methods with a user class, so that when you create a new user, they have those methods available to them as well.  

### How to create methods

List our methods inside the user class, but outside the constructor function.  Here we'll create a User class with login() and logout() methods:

    class User {
        constructor (email, name) {
            this.email = email;
            this.name = name;
        }

        login(){
            console.log(this.email, 'just logged in');
        }
        logout(){
            console.log(this.email, 'just logged out');
        }

    }

Now, every time we create a new user, we have access to these methods.

    userOne.login()
    userTwo.logout()

This will return:

    ryu@ninjas.com just logged in

    yoshi@mariokorp.com just logged out

## Method Chaining

What if we want to chain two or more methods together?  How do we do that?

Here's an example with an "updateScore" method that would add one to the "score" property in the User class:

    class User {
        constructor (email, name){
            this.email = email;
            this.name = name;
            this.score = 0;
    }
    login(){
        console.log(this.email, 'just logged in')
        return this;
    }
    logout(){
        console.log(this.email, 'just logged in')
        return this;
    } 
    updateScore(){
        this.score++
        console.log(this.email, 'score is now', this.score);
        return this;
    }
}

Notice that now each method returns "this".  By returning "this" at the end of the method, we can chain one method to another using the following syntax:

    userOne.login().updateScore().updateScore().logout();

## Class Inheritance

Say that in addition to the regular users, we want to some users to have admin privileges and have access to certain methods that aren't available to other users.  We want them to have all the same properties and methods of users with EXTRA methods like the ability to delete a user.  We don't want to list it with the other methods b/c then any user could delete a user.  

To solve this, we would use class inheritance.

First, create an admin class that will inherit from the User class. 

    class Admin extends user {

    }

Then we can pass in extra functionality that the User class does not have.

    class Admin extends user {
        deleteUser(user) {
            users = users.filter(u => {
                return u.email != user.email
            })
        }
    }

    var users = [userOne, userTwo];

Now we need to actually create an admin:

    var admin = new Admin('shaun@ninjas.com, 'shaun')
    
To implement the deleteUser() method:

    admin.deleteUser(userTwo);

What has actually happened?

    console.log(users)

This will log to the console:

    [User]
    0: User {
        email: "ryu@ninjas.com", name: "Ryu", score: 0;
    }

Notice that the second user (userTwo) has been deleted from the array of users.

## Constructors (under the hood)

ES6 classes are just a little syntactic sugar build on top of the JavaScript prototype model.  JavaScript as a language doesn't really have classes.  

The JavaScript prototype model was the original way we tend to create or emulate classes in JavaScript before we had the class keyword.  JavaScript is still using the prototype model under the hood.  It's important to understand the prototype model to really understand what is going on.

### Constructors

When we use the Class keyword, the constructor is responsible for making up the object when we want to create one based on that class.  That is the thing that binds all of the properties and values to the object.  So we'll still need a constructor function to construct the object under the prototype model.

    function User(email, name){
        this.email = email;
        this.name = name;
        this.online = false;
        this.login = function(){
            console.log(this.email, 'has logged in')
        }
    }

    var userOne = new User('ryu@ninjas.com', 'Ryu')
    var userTwo = new User('yoshi@mariokorp.com', 'Yoshi')

    console.log(userOne);
    userTwo.login();

    // User {email: 'ryu@ninjas.com', name: 'Ryu', online: false, login f}

    //yoshi@mariokorp.com has logged in

We're still kind of emulating a user class this way.  It's just that we aren't using the class keyword.  This is fine, but generally when we want to attach methods to a class like this, we don't put those methods inside the constructor function.  Instead, we use the prototype property on this constructor function.

## Javascript Prototype

Above, we attached a method (the login function) to the constructor function.  However, in a lot of cases, it's better to use the prototype property to add methods. Otherwise the method will be directly inside the object instead of being attached to the __proto__ property.

### Why is this important?

Every object type has a __proto__ type.  It's like a map for the object type.  It contains the functionality fo the object type.  It will know how to use the different methods.  We're not hardcoding the methods into each different user instance.  Instead,  we're defining them once on a single user prototype and then when a user object wants to use that method, it will know how to do that.  This way of working is more effecient and allows us later to use __proto__ type inheritance.

How do we access the prototype property? 

    User.prototype

Can't call prototype on the instances of the object. For example, userOne can't be written like this:

    userOne.prototype = new Uer('ryu@ninjas.com','Ryu')

In this case, userOne does not have a prototype property.  The instances have the __proto__ property, which points to the prototype.  Now we can attach method sto the prototype of User.  So instead of this (notice placement of login function):

    function User(email, name){
        this.email = email;
        this.name = name;
        this.online = false;
        this.login = function(){
        console.log(this.email, 'has logged in')
        }
    }

    var userOne = new User('ryu@ninjas.com', 'Ryu')
    var userTwo = new User('yoshi@mariokorp.com', 'Yoshi')


We would do this (again, notice placement of login function):

    function User(email, name){
        this.email = email;
        this.name = name;
        this.online = false;
    }

    User.prototype login = function(){
        this.online = true;
        console.log(this.email,'has logged in');
    }

    User.prototype logout = function(){
        this.online = false;
        console.log(this.email, 'has logged out');
    }

Now when you console log it, the login method is no longer directly inside the object.  It's now part of the __proto__ property.

### How would you add an admin class like above using the prototype model?

    function User(email, name){
        this.email = email;
        this.name = name;
        this.online = false;
    }

    User.prototype login = function(){
        this.online = true;
        console.log(this.email,'has logged in');
    }

    User.prototype logout = function(){
        this.online = false;
        console.log(this.email, 'has logged out');
    }

    function Admin(...args) {
        User.apply(this, args);
        this.role = 'super admin';
    }

    var userOne = new User('ryu@ninjas.com', 'Ryu');
    var userTwo = new User('yoshi@mariokorp.com', 'Yoshi');
    var admin = new Admin('shaun@ninjas.com', 'Shaun');

    When you console.log the admin, this is what you'll get:

        Admin { email: "shaun@ninjas.com", name: "Shaun", online: false, role:"super admin"}

The "role" property only applies to admins and will not appear when creating a regular User.

How do we get the methods (login, logout, etc.) to appear under the __proto__ property of admin?

    Admin.prototype = Object.create(User.prototype);


How would you add an extra method to admin that is not available to User?

    Admin.prototype.deleteUser = function(u){
        users = users.filter(user => {
            return user.email != u.email
        })
    };
# **T2A2 - API Webserver Project - Motor Racing API**

# Table of Contents

1. [Installation Guide](#installation-guide)
2. [What is the problem?](#what-is-the-problem?)
3. [Why is it a problem?](#why-is-it-a-problem?)
4. [Why PostgreSQL?](#why-postgresql)
5. [ORM](#orm)
6. [Endpoints for Motor Racing API](#endpoints-for-motor-racing-api)
7. [ERD](#erd)
8. [Third party services](#third-party-services)
9. [Models and Relationships](#models-and-relationships)
10. [Database Relations](#database-relations)
11. [Project Managment Methodology](#project-managment-methodology)
## Installation Guide

## What is the problem?
### R1 - Identification of the problem you are trying to solve by building this particular app.

High-profile motorsports such as Formula 1, Indy Car, and V8 Supercars are bolstered by extensive data infrastructure that provides in-depth information not only for the sport's participants but also for its fans. This availability of data enhances fans' ability to support and understand the sporting events they find engaging. However, a stark contrast emerges as we shift our focus from these top-tier professional sports to the more diverse world of amateur, semi-professional, club, virtual, and friend racing circles. As the variety of categories, vehicles, teams, circuits, and drivers dramatically increases, the ability to access data on these events becomes poorly managed, unintuitive, or inaccessible.

Whether it's a local karting championship, a club weekend at a circuit, or friends wishing to track their own virtual racing league, the lack of a comprehensive and accessible system for capturing, storing, and displaying data for these types of competitions becomes apparent. This deficiency is evidenced by the makeshift solutions, or lack of, currently employed by these communities. This shortfall not only hinders participants' ability to follow their results but also impacts spectators' engagement with these less-known categories of motorsport.

Typically, data for these semi-organized leagues are managed using rudimentary methods such as word documents, group chats, or even manually, with more casual groups often having less organization than this. There's no centrally managed, readily available system for people to access data about drivers, teams, circuits, races, results, and categories. Often, someone seeking information about a previous result must scroll through numerous social media posts in hopes of finding the comment that references the results. This approach is a disservice to these exciting events, as it heightens the barrier to entry for fans looking to connect with the sport and broaden their understanding of different communities.

The Motor Racing API aims to lay a foundation to rectify this problem. By creating an accessible and comprehensive system that stores data about various components of motor racing—and their interconnectedness—it caters to the needs of racers, teams, event organizers, and those interested in learning more about local competitions. This system is also beneficial for friend groups who simply want to maintain a well-kept record of their weekend ritual of battling it out at the local karting track. 

## Why is it a problem?
### R2 - Why is it a problem that needs solving?

At the core of this issue are two fundamental challenges that are in need of a resolution.

1. Reduced Engagement and Enjoyment
    - As with many sports, enjoyment goes beyond the event itself. Following sportspeople over a season of races, accessing statistics, and discovering intriguing information about the participants all enhance engagement and enjoyment. Currently, many lower-tier motor racing communities lack a comprehensive, approachable, or even discoverable platform for fans to delve deeper and find more information about races, teams, drivers, and circuits. By creating a tool that makes data more accessible, we pave the way for increased spectator engagement and enjoyment.

2. Restricted Growth of Communities
    - Most of these events or organizations spring from passion projects or weekend work by dedicated volunteers who aim to create competitive and enjoyable races. With this passion comes a lack of organization and substantial friction for new drivers, teams, sponsors, or races looking to get involved, primarily due to the organizers' limited resources. By introducing a platform that not only simplifies processing new drivers and teams into competitions but also serves as a central hub for sharing information about upcoming races and race results, we empower the community to grow.

The unique aspect of these communities and other lower-tier motorsport competitions is the harmonious blend of community and competition. Utilizing an API like the Motor Racing API enables these groups to foster a more interconnected and cohesive structure, while simultaneously enhancing accessibility and engagement with their fan base. This solution significantly broadens the level of participation that people can enjoy when following these events.

## Why PostgreSQL?
### R3 - Why have you chosen this database system. What are the drawbacks compared to others? 

The choice of a Relational Database Management System (RDBMS) for this application is most suitable due to the intrinsically relational nature of the data that will be stored. Racing data, which is composed of interconnected entities such as drivers, races, teams, circuits, and results, can be effectively modeled and managed within a relational database structure. An RDBMS, such as PostgreSQL, provides strong ACID compliance ensuring reliable transactions and maintaining data integrity.

PostgreSQL stands out among RDBMS options and has been chosen for this project. Its robustness, reliability, and ability to handle a vast amount of interconnected data make it an ideal choice. The popularity of PostgreSQL among developers leads to it being well documented, easing troubleshooting. It also boasts strong community support, enhancing its appeal due to the greater ability to find resources. 

Key features of PostgreSQL include its ability to efficiently process complex queries, which is essential for detailed analyses of race results. It's also extensible, enabling the addition of various functionalities and creating custom functions and data types. This flexibility allows it to cater to a wide range of use cases. Furthermore, PostgreSQL’s ACID compliance underscores the integrity and consistency of data transactions.

However, potential drawbacks should be considered. When compared to some other RDBMS, PostgreSQL exhibits slower read speeds. There may also be a steep learning curve during initial setup due to its complexity. Lastly, being an open-source system managed by multiple communities, PostgreSQL can occasionally present compatibility issues with certain setups.

In conclusion, despite its limitations, PostgreSQL benefits of robustness, ACID compliance, complex query handling, extensibility provide a compelling case for it to be used for this project. It aligns well with the nature of the data used for this case and makes it a great choice for this application. 


# Attached image of databases for this project with seeded data
## ORM
### R4 - Identify and discuss the key functionalities and benefits of an ORM

Object-Relational Mapping (ORM) is a technique that allows developers to interact with their database like a set of objects in their chosen programming language, providing several distinct advantages.

1. Language Consistency: ORMs enable developers to manipulate database entries using the syntax and idioms of their preferred programming language, such as Python, rather than writing raw SQL queries. This makes the code more readable and maintainable and allows developers to leverage their existing knowledge and skills more effectively.

2. Data Transformation: ORM handles the transformation between incompatible type systems (object-oriented and relational), simplifying the process of mapping database entries to objects in code. This can streamline the development process, reducing the likelihood of errors due to data type mismatches.

3. Database Agnosticism: By abstracting the underlying SQL commands, ORMs make it easier to switch between different types of databases with minimal changes to the codebase. This can be invaluable for projects that may need to scale or adapt to changing requirements in the future.

4. Security: The abstraction provided by ORMs also helps enhance security by reducing the risk of SQL injection attacks, as commands are parameterized, and strings aren't directly inserted into queries.

For this project, SQLAlchemy has been selected as the ORM. It is popular among python developers due to its ease of use and expansive features. It allows developers to work with a database like it is a set of Python objects.
## Endpoints for Motor Racing API
### R5 - Document all endpoints for your API
1. Login ('/login')
    - Method: POST
    - Required JSON Request Data:
      - 'email': User's email address
      - 'password': User's password
    - Expected JSON Response Data:
      - 'token': JWT token for the user session
      - 'user': Object containing user's email and name
    - Authentication: Not required 

2. Register ('/register')
    - Method: POST
    - Required JSON Request Data:
      - 'name': User's full name
      - 'email': User's email address
      - 'password': User's password
      - 'role': Role of the user (team, driver, organizer)
    - Expected JSON Response Data:
      - The newly registered user's data (excluding password)
    - Authentication: Not required

3. Get All Users ('/users')
   - Method: GET
   - Required JSON Request Data: None
   - Expected JSON Response Data:
     - An array of all users in the database (excluding their passwords)
   - Authentication: Required (JWT token and user must have 'admin' role)

4. Categories ('/categories')
- Get All Categories ('/')
    - Method:GET
    - Required JSON Request Data: 
        - None
    - Expected JSON Response Data: 
        - Array of all categories in the database
    - Expected HTTP Response Code: 200
    - Authentication: Not required
  
- Get Single Categories ('/<int:category_id>')
    - Method: GET
    - Required JSON Request Data:
        - None
    - Expected JSON Response Data: 
        - Object containing the details of the requested category
    - Expected HTTP Response Code: 200 (404 if not found)
    - Authentication: Not required

- Create a Category ('/')
    - Method: POST
    - Required JSON Request Data:
        - 'name': Name of the category
        - 'description': Description of the category
    - Expected JSON Response Data: 
        - Object containing the newly created category's data
    - Expected HTTP Response Code: 201 (400 if validation error, 400 if category already exists)
    - Authentication: Required (JWT token and user must have 'admin' or 'organizer' role)


- Update a Category('/<int:category_id>')
    - Method: PUT, PATCH
    - Required JSON Request Data:
        - Object containing category data to be changed
        -  'name' (New name for the category, string, optional)
        -  'description' (New description for the category, string, optional)
    - Expected JSON response data:
        - Object containing the updated category's data
    - Expected HTTP Response Code: 200 (400 if validation error, 404 if not found, 403 if unauthorized)
    - Authentication:
        - Required (JWT token and user must have 'admin' or 'organizer' role, or be the category owner)


- Delete a Category ('/<int:category_id>')
    - Method: DELETE
    - Required JSON Request Data:
    - Expected JSON response data:
        - Empty JSON object
    - Expected HTTP Response Code: 200 (404 if not found, 403 if unauthorized)
    - Authentication:
        - Required (JWT token and user must have 'admin' or 'organizer' role, or be the category owner)
 

## ERD
### R6 - An ERD for your app

## Third party services
### R7 - Detail any third party services that your app will use

1. [Flask](https://flask.palletsprojects.com/en/2.3.x/): Flask is the framework used for this API, providing a structure to handle routing and request mechanisms. The 'blueprint' function is also imported to to assist with organizing these routes. 
   ``from flask import Flask`` 
2. [Flask-SQLAlchemy](https://flask-sqlalchemy.palletsprojects.com/en/3.0.x/): SQLAlchemy is the ORM for this API. It is used extensively throughout the application when interacting with the databases without having to directly enter SQL commands. Operations such as 'select()`, 'add()', 'commit()', and 'delete()' are used.
    ``from flask_sqlalchemy import SQLAlchemy``
3. [Flask-Marshmallow](https://flask-marshmallow.readthedocs.io/en/latest/): Marshmallow is used to serialize and deserialize data types into simpler, Python-friendly formats. Marshmallow schemas are also being used, which is a blueprint for how to serialize and deserialize data for a particular model. 
    ```
   class TeamSchema(ma.Schema):
    drivers = ma.Nested('DriverSchema', many=True, only=('id', 'first_name', 'last_name'))
    user= ma.Nested('UserSchema', only=('id',))
    class Meta:
        fields = ('id','name', 'year_founded', 'drivers', 'user', 'user_id') 
    ``` 
4. [Flask-JWT-Extended](https://flask-jwt-extended.readthedocs.io/en/stable/): This third party service assists in providing functionality surronding JSON web tokens (JWT). It is being used in this application to create access tokens for certain methods that require authetnication. My version: "The jwt_required() decorator is used to protect specific routes, and get_jwt_identity() retrieves the login information of the currently authenticated user. This allows for greater security around particular functions of the application. 
    ```
    @jwt_required()
    def admin_or_organizer_role_required():
    user_id = get_jwt_identity()
    stmt = db.select(User).filter_by(id=user_id)
    user =db.session.scalar(stmt)
    if not user:
        abort(400, 'User not found.')
    if not (user.is_admin or user.role == 'organizer'):
        abort(400, 'Admin or Organizer can only perform this function.')
    return user
    ```

5. [Flask-Bcrypt](https://flask-bcrypt.readthedocs.io/en/1.0.1/): Bcrypt provides support for hashing and protecting passwords. It is used in creating the password hash with ``generate_password_hash()`` as well as in the login process with ``check_password_hash()``. Overall BCrpyt is very helpful in helping to ensure the security and privacy of users. 
    ```
    @auth_bp.route('/login', methods=['POST'])
    def login():
    try:
        stmt = db.select(User).filter_by(email=request.json['email'])
        user = db.session.scalar(stmt)
        if user and bcrypt.check_password_hash(user.password, request.json['password']):
            token = create_access_token(identity=user.id, expires_delta=timedelta(days=1))
            return {'token': token, 'user': UserSchema(only=['email','name']).dump(user)}, 200
        else:
            return {'error': 'Invalid email or password'}, 401
    except KeyError:
        return {'error': 'Invalid email or password'}, 401
    ``` 


## Models and Relationships
### R8 - Describe your projects models in terms of the relationships they have with each other

This project uses various models to store and manage data effectively from the variety of tables. The database uses SQLAlchemy, a Python-based ORM that helps with data handling. The primary models of this API are User, Driver, Team, Category, Circuit, Race, and Result. 

1. **User**: This is the cornerstone of the application. I designed it to have relationships with almost all the other models. It comprises fields for user identification and authentication (name, email, password, role, is_admin). I have established one-to-many relationships from the User model to Driver, Team, Category, Circuit, Race, and Result models. This design implies that a single user can own multiple instances of these entities based on their access level.
    ```
    class User(db.Model):
        __tablename__ = 'users'

        id = db.Column(db.Integer, primary_key=True)
        name = db.Column(db.String)
        email = db.Column(db.String, nullable=False, unique=True)
        password = db.Column(db.String, nullable=False)
        role = db.Column(db.String, nullable=True)

        is_admin = db.Column(db.Boolean, default=False)

        driver = db.relationship('Driver', back_populates='user')
        team = db.relationship('Team', back_populates='user')
        category = db.relationship('Category', back_populates='user')
        circuits = db.relationship('Circuit', back_populates='user')
        races = db.relationship('Race', back_populates='user')
        results = db.relationship('Result', back_populates='user')
    ```
2. **Driver**: This model represents the drivers in the various racing communities who use this API. It exhibits a one-to-many relationship with Result, indicating that a driver can have multiple race results. Furthermore, it has a many-to-one relationship with Team and User, meaning each driver is associated with a specific team and user.
   ```
    class Driver(db.Model):
        __tablename__ = 'drivers'

        id = db.Column(db.Integer, primary_key=True)

        date_of_birth = db.Column(db.Date())
        first_name = db.Column(db.String)
        last_name = db.Column(db.String)
        nationality = db.Column(db.String)

        team_id = db.Column(db.Integer, db.ForeignKey('teams.id'), nullable=True)
        team = db.relationship('Team', back_populates='drivers')

        user_id = db.Column(db.Integer, db.ForeignKey('users.id'))
        user = db.relationship('User', back_populates='driver')

        results = db.relationship('Result', back_populates='driver', cascade='all, delete-orphan')
   ```
3. **Team**: I used this model to represent the teams in the application. A team has a one-to-many relationship with Driver and a many-to-one relationship with User. This arrangement means a team can consist of multiple drivers but is owned by one user.
   ```
    class Team(db.Model):
        __tablename__ = 'teams'

        id = db.Column(db.Integer, primary_key=True)

        name = db.Column(db.String, nullable=False, unique=True)
        year_founded = db.Column(db.Integer)

        user_id = db.Column(db.Integer, db.ForeignKey('users.id'))
        user = db.relationship('User', back_populates='team')

        drivers = db.relationship('Driver', back_populates='team')
   ```
4. **Category**: This model represents different race categories. It maintains a one-to-many relationship with Race, as a category can correspond to multiple races. Each category is linked to a single user through a many-to-one relationship.
   ```
    class Category(db.Model):
        __tablename__ = 'categories'

        id = db.Column(db.Integer, primary_key=True)

        name = db.Column(db.String, nullable=False, unique=True)
        description = db.Column(db.String)

        races = db.relationship('Race', back_populates='category')

        user_id = db.Column(db.Integer, db.ForeignKey('users.id'))
        user = db.relationship('User', back_populates='category')
   ```
5. **Circuit**: This model embodies the racing circuits or tracks. A circuit can be associated with multiple races, exhibiting a one-to-many relationship with Race. Also, each circuit is connected to a single user. 
   ```
    class Circuit(db.Model):
        __tablename__ = 'circuits'

        id = db.Column(db.Integer, primary_key=True)

        track_name = db.Column(db.String, nullable=False, unique=True)
        location = db.Column(db.String)
        lap_record = db.Column(db.Integer)

        user_id = db.Column(db.Integer, db.ForeignKey('users.id'))
        user = db.relationship('User', back_populates='circuits')

        races = db.relationship('Race', back_populates='circuit')

   ```
6. **Race**: This model encapsulates the races. Each race has multiple outcomes, indicating a one-to-many relationship with Result. This means each race can produce multiple results, where each result represents the performance of a specific driver in the race. Furthermore, each race is associated with one Circuit, one Category, and one User, creating many-to-one relationships.
   ```
    class Race(db.Model):
        __tablename__ = 'races'

        id = db.Column(db.Integer, primary_key=True)

        date = db.Column(db.Date, nullable=False)
        name = db.Column(db.String, nullable=False)

        circuit_id = db.Column(db.Integer, db.ForeignKey('circuits.id'),nullable=False)
        circuit = db.relationship('Circuit', back_populates='races')

        category_id = db.Column(db.Integer, db.ForeignKey('categories.id'), nullable=False)
        category = db.relationship('Category', back_populates='races')

        user_id = db.Column(db.Integer, db.ForeignKey('users.id'))
        user = db.relationship('User', back_populates='races')

        results = db.relationship('Result', back_populates='race')

   ```
7. **Result**: This model records the outcomes of the races. It has many-to-one relationships with Driver, Race, and User, meaning each race result is associated with a specific driver, race, and user.
   ```
    class Result(db.Model):
        __tablename__ = 'results'

        id = db.Column(db.Integer, primary_key=True)

        start_position = db.Column(db.Integer, nullable=False)
        end_position = db.Column(db.Integer, nullable=False)
        points = db.Column(db.Integer)

        race_id = db.Column(db.Integer, db.ForeignKey('races.id'))
        race = db.relationship('Race', back_populates='results')

        driver_id = db.Column(db.Integer, db.ForeignKey('drivers.id', ondelete='CASCADE'), nullable=False)
        driver = db.relationship('Driver', back_populates='results')

        user_id = db.Column(db.Integer, db.ForeignKey('users.id'))
        user = db.relationship('User', back_populates='results')
   ```

The relationships between these models are vital to the functionality of the application as they offer the flexibility to make complex queries and data retrievals across different entities. These interconnections also define the data structure and are pivotal in its functionality. 
## Database Relations
### R9 - Discuss the database relations to be implemented in your application
 
## Project Managment Methodology
### R10 - Describe the way tasks are allocated and tracked in your project


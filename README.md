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

## ERD
### R6 - An ERD for your app

## Third party services
### R7 - Detail any third party services that your app will use

## Models and Relationships
### R8 - Describe your projects models in terms of the relationships they have with each other

## Database Relations
### R9 - Discuss the database relations to be implemented in your application
 
## Project Managment Methodology
### R10 - Describe the way tasks are allocated and tracked in your project


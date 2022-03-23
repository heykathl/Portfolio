# Databases - Modelling a database to satisfy user stories

## Learning objectives

An exercise to learn three things:

1. Explain what a database model is.
2. Model a database to comply to user stories.
3. Explore different ways data can be stored and compare their merits.

## Three types of database relationships

### One-to-one relationships
When each record of one table is related to only one record of the other table
For example, there are two entities (Person: Id, Name, Age, Address) and (Passport: Passport_id, Passport_no). Each person can only have one passport and each passport belongs to only one person.
These relationships are used for security purposes which may store sensitive data, hidden from certain users. 

### One-to-many relationships
When each record of the one table of one table can be related to one or more than one record of another table. 
In a relational database system, a one-to-many table relationship links two tables based on a Foreign Key column in the child which references the Primary Key of the parent table row.
For example, a Customer entity can have more than one Account entity, however an Account entity can is only associated with one Customer.

### Many-to-many relationships
When each record of the first table can be related to one or more than one record of the second table. 
In a relational database system, a many to many table relationship would link two parent tables which would contain two foreign key columns, which references the primary key of the two parent tables. 
For example, a Blog Post entity would have have tags and a Tag entity would have many blog posts. 

```
As a coach
So I can get to know all students
I want to see a list of students' names
```
<img width="637" alt="Screenshot 2022-03-17 at 11 40 25" src="https://user-images.githubusercontent.com/74867241/158801122-fa1d25fb-e135-428e-84f1-782fe3e4a488.png">

```
As a coach
So I don't get overwhelmed with a massive list of everyone
I want to filter the list of students by cohort name
```
<img width="641" alt="Screenshot 2022-03-17 at 11 41 29" src="https://user-images.githubusercontent.com/74867241/158801242-01258a54-d802-4d90-ab62-3e37377b186b.png">

```
As a coach
So I can prepare for Day One and Demo Day
I want to see the start date and demo day date of a cohort
```
<img width="638" alt="Screenshot 2022-03-17 at 11 41 50" src="https://user-images.githubusercontent.com/74867241/158801285-b7325011-41f0-4c52-86e7-7f5dc0f93223.png">

```
As a coach
So I can link a name to a face
I want to see a URL with their picture next to each student
```
<img width="635" alt="Screenshot 2022-03-17 at 11 42 17" src="https://user-images.githubusercontent.com/74867241/158801356-4baa23eb-89bf-4cdc-a103-9099f8e3a14c.png">

```
As a coach
So I can tag certain students
I want to tag a student with many named tags (like "happy" or "ok")
```
<img width="636" alt="Screenshot 2022-03-17 at 11 42 55" src="https://user-images.githubusercontent.com/74867241/158801438-f72d488c-f250-4f3a-80bd-b7b3170f3313.png">
As you can see highlighted in red, I was unsure how to complete this user story.


```
As a coach
So I can see students with the same tag
I want to filter students in the list by tag name
```
<img width="624" alt="Screenshot 2022-03-17 at 11 43 31" src="https://user-images.githubusercontent.com/74867241/158801528-53691e13-7023-495e-b263-f3d35b7daa68.png">


```
As a student
So I can reflect on my days
I want to rate each day out of 10
```

```
As a coach
So I can get an overview of how students are feeling
I want to see an average of the day ratings for each student
```


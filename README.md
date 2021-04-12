# course-planning-lang

Students are usually required to take courses that have prerequisites and corequisites. It is often hard to plan manually what would be the best way to take your classes while at the same time checking what are the prereqs for each class. That is why I propose building a programming language that is English-like that will facilitate the work of advisers and students to plan their courses through each semester to be able to graduate on time.

We can declare classes and their respective relationships as follows:

```
#in this block we define all the relationships between classes

# we can use one-liner for simple associations
class CSCE221(3) is PREREQ for CSCE431

#another one-liner
class CSCE315(3), CSCE221(3) are PREREQ for CSCE431

#or we can build them in this fashion which may be more readable
class CSCE315(3) has
  CSCE221(3) as COREQ
  CSCE121(3) as PREREQ
end

```

We can declare a coursework like this
```
#we can define a simple coursework with all the classes that it posseses
courseload CORE has
  GOVT101
  GOVT102
  ....
end

#we can also create a coursework using another course work as base, look at CORE below:
courseload CSCE_MAJOR has
  CORE
  CSCE121
end

```

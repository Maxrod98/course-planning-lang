# course-planning-lang

Students are usually required to take courses that have prerequisites and corequisites. It is often hard to plan manually what would be the best way to take your classes while at the same time checking what are the prereqs for each class. That is why I propose building a programming language that is English-like that will facilitate the work of advisers and students to plan their courses through each semester to be able to graduate on time.

We can declare classes and their respective relationships as follows:

```
#in this block we define all the relationships between classes

# we can use one-liner for simple associations
class CSCE221(3) is prereq for CSCE431

#another one-liner
class CSCE315(3), CSCE221(3) are prereq for CSCE431

#or we can build them in this fashion which may be more readable
class CSCE315(3) has
  CSCE221(3) as coreq
  CSCE121(3) as prereq
end

```

We can declare a coursework like this
```
#we can define a simple coursework with all the classes that it posseses
courseload CORE has
  GOVT101
  GOVT102
  ...
end

#we can also create a coursework using another course work as base, look at CORE below:
courseload CSCE_MAJOR has
  CORE
  CSCE121
  ...
end

#in the following, NEW_MAJOR keeps all the classes from CSCE_MAJOR without the CORE classes 
courseload NEW_MAJOR is CSCE_MAJOR - CORE

```

What about planning out a semester once we have a coursework? Well, remember our previous class declaration
```
class CSCE315(3) has
  CSCE221(3) as coreq
  CSCE121(3) as prereq
end

#nested implementation

CSCE315(3) has
  CSCE221(3) as coreq
  CSCE121(3) as prereq
end


#I wrote down the second year fo Texas A&M computer science:

class PROGRAMMING_COURSE(3)

class CSCE121(4) has
  PROGRAMMING_COURSE(3) as prereq
end

class CSCE121(1)

class CSCE222(3), ECEN222(3) has
  MATH151 as prereq
end

class MATH304(3) has
  MATH148 or MATH152 or MATH172 as prereq
  JUNIOR
end

#TODO: how are we going to fill in things like science courses electives

```

How can a student use this programming language right away?



How will this language facilitate planning compared to a flowchart?





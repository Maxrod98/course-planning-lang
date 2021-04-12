# course-planning-lang

Students are usually required to take courses that have prerequisites and corequisites. It is often hard to plan manually what would be the best way to take your classes while at the same time checking what are the prereqs for each class. That is why I propose building a programming language that is English-like that will facilitate the work of advisers and students to plan their courses through each semester to be able to graduate on time.

We can declare classes and their respective relationships as follows:

```
#in this block we define all the relationships between courses

# we can use one-liner for simple associations
course CSCE221(3) is prereq for CSCE431(3)

#another one-liner
course CSCE315(3), CSCE221(3) are prereq for CSCE431(3)

#or we can build them in this fashion which may be more readable
course CSCE315(3) has
  CSCE221(3) as coreq
  CSCE121(3) as prereq
end

```

We can declare a coursework like this
```
#we can define a simple coursework with all the courses that it posseses
courseload CORE has
  GOVT101
  GOVT102
  ...
end

courseload CSCE_SYSTEMS_TRACK has
  CSCE410
  CSCE456
  CSCE462
  CSCE463
  CSCE464
  CSCE465
  CSCE469
END

#we can also create a coursework using another course work as base, look at CORE below:
courseload CSCE has
  CORE
  CSCE121  
  ...
end

#in the following, NEW_MAJOR keeps all the courses from CSCE_MAJOR without the CORE courses 
courseload NEW_MAJOR is CSCE_MAJOR - CORE

```

What about planning out a semester once we have a coursework? Well, remember our previous course declaration
```
#I wrote down the second year fo Texas A&M computer science:

course PROGRAMMING_COURSE(3)

course CSCE121(4) has
  PROGRAMMING_COURSE(3) as prereq
end

course CSCE121(1)

course CSCE222(3), ECEN222(3) has
  MATH151 as prereq
end

course MATH304(3) has
  MATH148 or MATH152 or MATH172 as prereq
  JUNIOR
end

#TODO: how are we going to fill in things like science courses electives

```

How can a student use this programming language right away?

```
#A more in depth script for the CSCE 2017 Texas A&M catalog:

courseload CSCE_SYSTEMS_TRACK has
  CSCE410
  CSCE456
  CSCE462
  CSCE463
  CSCE464
  CSCE465
  CSCE469
end

courseload CSCE_ALGORITHMS_TRACK has
  CSCE411
  CSCE433
  CSCE440
  CSCE442
end

courseload SEVENTH_COURSE has
  CSCE491
  ENGR385
  ENGR270
  ENGR470
end

#... explicitly give more

#notice how we use the clause "of"
courseload CSCE_UPPER_TRACK has

  courseload ALL_UPPER_TRACK has
    CSCE_SYSTEMS_TRACK
    CSCE_SOFTWARE_TRACK
    CSCE_INFORMATION_TRACK
    CSCE_ALGORITHMS_TRACK
  end
  
  1 of CSCE_SYSTEMS_TRACK
  1 of CSCE_SOFTWARE_TRACK
  1 of CSCE_INFORMATION_TRACK
  2 of ALL_UPPER_TRACK
  3 credits of ALL_UPPER_TRACK or 1 of SEVENTH_COURSE
  CSCE411
end

```

How will this language facilitate planning compared to a flowchart?
How to

```
#repeats will result in an error, like so:

courseload CSCE_SYSTEMS_TRACK has
  CSCE410
  CSCE410 #there is a compilation error here
END


```

# HW-NoSQL-MongoDB

## Create database
``` 
    use StudentCourse 
```

## Insert data
``` 
    db.StudentCourse.insertMany([
    {"name":"Ramesh","subject":"maths","marks":87},
    {"name":"Ramesh","subject":"english","marks":59},
    {"name":"Ramesh","subject":"science","marks":77},
    {"name":"Rav","subject":"maths","marks":62},
    {"name":"Rav","subject":"english","marks":83},
    {"name":"Rav","subject":"science","marks":71},
    {"name":"Alison","subject":"maths","marks":84},
    {"name":"Alison","subject":"english","marks":82},
    {"name":"Alison","subject":"science","marks":86},
    {"name":"Steve","subject":"maths","marks":81},
    {"name":"Steve","subject":"english","marks":89},
    {"name":"Steve","subject":"science","marks":77},
    {"name":"Jan","subject":"english","marks":0,"reason":"absent"}]) 
 ```

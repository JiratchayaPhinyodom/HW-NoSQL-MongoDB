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
 ## StudentCourse Database
 ```
 [
  {
    _id: ObjectId("64297ac6fe95819a62201375"),
    name: 'Ramesh',
    subject: 'maths',
    marks: 87
  },
  {
    _id: ObjectId("64297ac6fe95819a62201376"),
    name: 'Ramesh',
    subject: 'english',
    marks: 59
  },
  {
    _id: ObjectId("64297ac6fe95819a62201377"),
    name: 'Ramesh',
    subject: 'science',
    marks: 77
  },
  {
    _id: ObjectId("64297ac6fe95819a62201378"),
    name: 'Rav',
    subject: 'maths',
    marks: 62
  },
  {
    _id: ObjectId("64297ac6fe95819a62201379"),
    name: 'Rav',
    subject: 'english',
    marks: 83
  },
  {
    _id: ObjectId("64297ac6fe95819a6220137a"),
    name: 'Rav',
    subject: 'science',
    marks: 71
  },
  {
    _id: ObjectId("64297ac6fe95819a6220137b"),
    name: 'Alison',
    subject: 'maths',
    marks: 84
  },
  {
    _id: ObjectId("64297ac6fe95819a6220137c"),
    name: 'Alison',
    subject: 'english',
    marks: 82
  },
  {
    _id: ObjectId("64297ac6fe95819a6220137d"),
    name: 'Alison',
    subject: 'science',
    marks: 86
  },
  {
    _id: ObjectId("64297ac6fe95819a6220137e"),
    name: 'Steve',
    subject: 'maths',
    marks: 81
  },
  {
    _id: ObjectId("64297ac6fe95819a6220137f"),
    name: 'Steve',
    subject: 'english',
    marks: 89
  },
  {
    _id: ObjectId("64297ac6fe95819a62201380"),
    name: 'Steve',
    subject: 'science',
    marks: 77
  },
  {
    _id: ObjectId("64297ac6fe95819a62201381"),
    name: 'Jan',
    subject: 'english',
    marks: 0,
    reason: 'absent'
  }
]
```
## Find the total marks for each student across all subjects.
```
db.StudentCourse.aggregate([{$group: { _id: '$name', total_marks: { $sum: '$marks' }}}])
```
### The result of total marks for each student across all subjects.
```
[
  { _id: 'Alison', total_marks: 252 },
  { _id: 'Jan', total_marks: 0 },
  { _id: 'Ramesh', total_marks: 223 },
  { _id: 'Rav', total_marks: 216 },
  { _id: 'Steve', total_marks: 247 }
]
```
## Find the maximum marks scored in each subject.
```
db.StudentCourse.aggregate([{$group: { _id: '$subject', max_score: { $max: '$marks' }}}])
```
### The result of the maximum marks scored in each subject.
```
[
  { _id: 'maths', max_score: 87 },
  { _id: 'science', max_score: 86 },
  { _id: 'english', max_score: 89 }
]
```
## Find the minimum marks scored by each student.
```
db.StudentCourse.aggregate([{$group: { _id: '$name', min_score: { $min: '$marks' }}}])
```
### The result of the minimum marks scored by each student.
```
[
  { _id: 'Alison', min_score: 82 },
  { _id: 'Jan', min_score: 0 },
  { _id: 'Ramesh', min_score: 59 },
  { _id: 'Rav', min_score: 62 },
  { _id: 'Steve', min_score: 77 }
]
```
## Find the top two subjects based on average marks.
```
db.StudentCourse.aggregate([{$group: { _id: '$subject', avg_marks: { $avg: '$marks' }}}, {$sort: {avg_marks: -1}}, {$limit: 2}])
```
### The result of the top two subjects based on average marks.
```
[
  { _id: 'maths', avg_marks: 78.5 },
  { _id: 'science', avg_marks: 77.75 }
]
```

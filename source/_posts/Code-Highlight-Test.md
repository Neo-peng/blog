title: Code Highlight Test
author: John Doe
date: 2022-05-15 06:51:47
tags:
cover: https://cdn.jsdelivr.net/gh/jerryc127/CDN@latest/cover/default_bg.png
---
```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

``` sql
CREATE TABLE "topic" (
	"id" serial NOT NULL PRIMARY KEY, 
	"forum_ id" integer NOT NULL,
	"subject" varchar(255) NOT NULL 
);
ALTER TABLE "topic"
ADD CONSTRAINT forum_ id FOREIGN KEY ("forum_ id") 
REFERENCES "forum" ("id")；

-- Initials
insert into “topic" ("forum_ id",“subject") 
values (2, 'D' 'artagnian");
```

``` js
var foo = function (bar) {
  return bar++;
};
```

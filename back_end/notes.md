# Databases

## N+1 Problem

https://semaphoreci.com/blog/2017/08/09/faster-rails-eliminating-n-plus-one-queries.html

```ruby
query = User.limit(10)

query.each do |user|
  puts #{user.id}
end
```

## Database Normalization

https://towardsdatascience.com/database-normalization-explained-53e60a494495

_MAIN IDEA: Data ought to be organized in order to easily write reliable CRUD logic._

**First normal form**
* Individual columns are in most reduced state. IE: The data needs max 1 column to contain it.
* Rows are uniquely identified.
* No repeating groups of columns. Example of violation: `author1_name`, `author1_location`, `author2_name`, `author2_location`. 

**Second normal form**
* All the data must relate to the primary key.

Otherwise, you might forget to update the unrelated column:
```
Customer
--------
id
company_name
contact_person_name <=== should be own table
contact_person_role <=== should be own table
```

**Third normal form**
* Each column must be non-transitively dependent. All columns should only depend on the primary key. Again, otherwise, you might forget to update the column.

```
People
------
id
first_name
last_mame
city <=== this depends on postal_code
postal_code
```

# APIs

## HATEOAS

http://restcookbook.com/Basics/hateoas/

API responds with options along with routes.

EG:
* CLIENT: What is my bank account balance?
* API: $xxx. Here are some routes for withdrawing and depositing.
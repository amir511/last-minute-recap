# Data normalization vs denormalization
Yes, data denormalization is a technique used in database design to optimize query performance by duplicating data and breaking normalization rules. Here's a practical use case of data denormalization:

Consider a large e-commerce website with millions of products and users. One of the most common queries is to display a product along with its reviews and ratings. To achieve this, the website would need to join multiple tables, such as products, reviews, and users, which can be a time-consuming operation.

To improve query performance, the website could denormalize the data by creating a single table that combines all the relevant information for a product, including its reviews and ratings. This denormalized table could include redundant data such as the product name, description, and other attributes that are also stored in other tables.

By denormalizing the data, the website can reduce the number of joins needed to retrieve the information and improve query performance. However, denormalization also comes with the cost of increased storage space and the need to keep redundant data in sync.

In summary, denormalization is a trade-off between query performance and storage space, and it should be used judiciously based on the specific needs of the application.

# SQL joins
https://www.w3schools.com/sql/sql_join.asp
https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-joins/#:~:text=PostgreSQL%20join%20is%20used%20to,columns%20of%20the%20second%20table.


# Sql advancd queries
Aggregation

annotation

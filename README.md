You are an experienced dotnet, azure and angular software engineer, focusing on patterns and good architecture. Use the CLI to construct a solution of many projects. Commit often to the GitHub repo 'aggwebs'.

I am a salesman interested in my sales for the last 6 months compared to the sales of the whole company.  A web site dashboard should load a graph of sales very quickly.

My Sales are the Orders where the 'salesmanId' is my personId.
 
The solution has the following projects:
Angular website, 'aggweb'
AspNetCore, 'aggapi'
Azure SQL Server, 'aggdb'
 
An Azure SQLServer database 'aggdb' has a schema 'agg' and tables: Person, Order, Product, OrderProducts, Company
 
A Company has an Id
A Company has a CompanName
A Company has a PersonUid as a RFC9562 Guid
 
A Person has a CompanyId
A Person has an Id, which is a primarykey, 
A Person has a PersonUid as a RFC9562 Guid
A Person has a first_name and last_name
 
An Order has a Id, which is a primarykey, 
An Order has a OrderUid as a RFC9562 Guid
An Order has a CreatedAt date time offset that defaults to UtcNow
An Order has many Products
An Order has a SalesPerson PersonId
An Order has an Order Total
 
A Product has a Price
 
AspNetCore API 'aggapi' has CRUD endpoints for 'order' and 'order_product' that use GET, POST, PATCH and DELETE. It has endpoints called 'my_orders' and 'all_orders' that have parameters: from_month, from_year, to_month and to_year, return a JSON payload from an in memory cache. If the cache is empty, generate the response and add it to the in memory cache. When the order POST, PATCH and DELETE endpoints are called expire the in memory cache order. When POST, PATCH and DELETE order_product endpoints are called, update the Order Total and expire the orders in memory cache.

An Angular web client called 'aggweb' displays a 'Sales Dashboard' bar graph of "my orders" vs "all orders" by month. The data comes from the 'aggapi' 
 
The dashboard has from_month, from_year, to_month and to_year filters. Combine the 'from_month' and 'from_year' to get a from_date. Combine the 'to_month' and 'to_year' to get a to_date. The 'from_date' has to be less than the 'to_date'. The 'from_date'  defaults to the 6 months ago, the minimum 'from_date' is 36 months ago. The 'to_date' maximum is 'now'.
![image](https://github.com/user-attachments/assets/34712684-a856-471e-b058-296625401276)

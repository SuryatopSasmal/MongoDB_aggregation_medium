# MongoDB_aggregation_medium
### Medium Difficulty

**1. Total Quantity of Products by Supplier:**

- **Task:** Write an aggregation query to calculate the total `quantity` of products supplied by each `supplier.name`.
- **Hint:** Use `$group` on `supplier.name` and `$sum` on `quantity`.
- **Expected Output (order might vary):**
<pre>
  db.products.aggregate([
  {
    $group: {
      _id: "$supplier.name",
      totalQuantity: { $sum: "$quantity" }
    }
  }
]);
</pre>
![image](https://github.com/user-attachments/assets/e7a22352-74ef-43d7-aeda-5ce1fd3f7f12)
**2. Average Price of Products per Tag:**

- **Task:** Write an aggregation query to find the average `price` of products associated with each `tag`. List the tag and its average price, sorted by average price in descending order.
- **Hint:** Use `$unwind` on `tags`, then `$group` on tags, and `$avg` on price. Finally, `$sort`.
- **Expected Output (approximate, floating point precision might vary slightly):**
<pre>
  db.products.aggregate([
  {
    $unwind: "$tags"
  },
  {
    $group: {
      _id: "$tags",
      averagePrice: { $avg: "$price" }
    }
  },
  {
    $sort: {
      averagePrice: -1
    }
  }
]);
</pre>
![image](https://github.com/user-attachments/assets/ad3a35fe-d382-4cfe-aed0-62d34ccb5d7d)
**3. Product Names and Prices, Sorted by Price (Descending):**

- **Task:** Write an aggregation query to display only the `name` and `price` of each product, sorted by `price` from highest to lowest. Do not include the `_id` field.
- **Hint:** Use `$project` and `$sort`.
- **Expected Output:**
<pre>
  db.products.aggregate([
  {
    $project: {
      _id: 0,
      name: 1,
      price: 1
    }
  },
  {
    $sort: {
      price: -1
    }
  }
]);
</pre>
![image](https://github.com/user-attachments/assets/85d11566-2e24-45ba-a983-a04ae554d75d)
![image](https://github.com/user-attachments/assets/281f41d1-3cae-426a-a1d8-18453d020836)


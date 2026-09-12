# SQL Mini Analysis
---

- Data source : Bigquery Public Dataset
- Dataset : The look E-commerce

created by : Riki

## Analysis

### 1. Mengetahui Berapa banyak item yang tercatat pada database?

 **Syntax**

 ```sql
 SELECT
  COUNT(id) AS jumlah_items
FROM
  bigquery-public-data.thelook_ecommerce.order_items;
```

**Ouput**

terdapat sebanyak 181.589 item yang tecatat dalam transaksi the look commerce

### 2. Top 3 kategori produk yang tercatat ?
**Syntax**

```sql
SELECT
  p.category,--non-agg
  COUNT(oi.id) AS jumlah_items --agg
FROM
  bigquery-public-data.thelook_ecommerce.order_items AS oi
JOIN
  bigquery-public-data.thelook_ecommerce.products AS p
ON oi.product_id = p.id
GROUP BY p.category
ORDER BY jumlah_items ASC;
```

**Output**
- Top 3 : Intimates (13.529), Jeans (12.595), Tops & Tees (11.946)
- Last 3 : Clothing Sets (220), Jumpsuits & Rompers (901), Suits (972)

### 3. Kategori produk yang paling banyak terjual/komplit ?
**Syntax**

```sql
SELECT
  p.category,
  COUNT(oi.id) AS jumlah_items
FROM
  bigquery-public-data.thelook_ecommerce.order_items AS oi
JOIN
  bigquery-public-data.thelook_ecommerce.products AS p
ON oi.product_id = p.id
WHERE
  oi.status = 'Complete'
GROUP BY p.category
ORDER BY jumlah_items DESC;
```

**Output**

- TOP 3 : Intimates (3.396), Jeans(3.073), Fashion Hoodies & Sweatshirts (2.891)

### 4. Kategori produk yang paling sering dibatalkan ?
**Syntax**

```sql
SELECT
  p.category,
  COUNT(oi.id) AS jumlah_items
FROM
  bigquery-public-data.thelook_ecommerce.order_items AS oi
JOIN
  bigquery-public-data.thelook_ecommerce.products AS p
ON oi.product_id = p.id
WHERE
  oi.status = 'Cancelled'
GROUP BY p.category
ORDER BY jumlah_items DESC;
```

**Output**

- Top 3 : Intimates (1,969), jeans (1.927) Top & Tees (1.855)

### 5. Kategori produk yang paling sering dikembalikan?
**Syntax**
```sql
SELECT
  p.category,
  COUNT(oi.id) AS jumlah_items
FROM
  bigquery-public-data.thelook_ecommerce.order_items AS oi
JOIN
  bigquery-public-data.thelook_ecommerce.products AS p
ON oi.product_id = p.id
WHERE
  oi.status = 'Returned'
GROUP BY p.category
ORDER BY jumlah_items DESC;
```

**Output**

- Top 3 : Jeans (1.312), Intimates (1.309) Swim (1.192)












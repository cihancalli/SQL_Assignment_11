# SQL_Assignment_11

## Sorgu Senaryoları

* actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

```bash
SELECT first_name
FROM actor
UNION
SELECT first_name
FROM customer
ORDER BY first_name;
```



* actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

```bash
SELECT first_name
FROM actor
INNER JOIN customer ON actor.first_name = customer.first_name
ORDER BY first_name;
```



* actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

```bash
SELECT first_name
FROM actor
LEFT JOIN customer ON actor.first_name = customer.first_name
WHERE customer.first_name IS NULL
ORDER BY first_name;
```



* İlk 3 sorguyu tekrar eden veriler için de yapalım.
* Tüm verileri sıralayalım.

```bash
SELECT first_name
FROM (
  SELECT first_name
  FROM actor
  UNION
  SELECT first_name
  FROM customer
) AS t
GROUP BY first_name
HAVING COUNT(*) > 1
ORDER BY first_name;
```

* Kesişen verileri sıralayalım.

```bash
SELECT first_name
FROM actor
INNER JOIN customer ON actor.first_name = customer.first_name
GROUP BY first_name
HAVING COUNT(*) > 1
ORDER BY first_name;

```

* İlk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

```bash
SELECT first_name
FROM actor
LEFT JOIN customer ON actor.first_name = customer.first_name
WHERE customer.first_name IS NULL
GROUP BY first_name
HAVING COUNT(*) > 0
ORDER BY first_name;
```

Not: Bu sorgular, dvdrental örnek veri tabanı üzerinde çalıştırılmıştır. Farklı bir veri tabanı kullanıyorsanız, tablo adlarını ve sütun adlarını buna göre değiştirmeniz gerekir.
## Status quo

**Products**:

	| id | name      |
	|----|-----------|
	| 1  | Product 1 |
	| 2  | Product 2 |
	| 3  | Product 3 |

**Prices**:

	| id | Product_id | created_at          | prices |
	|----|------------|---------------------|--------|
	| 1  | 1          | 2017-12-23 08:32:11 | 10     |
	| 2  | 1          | 2017-11-21 03:33:10 | 12     |
	| 3  | 2          | 2017-12-23 08:32:11 | 43     |
	| 4  | 2          | 2017-11-21 03:33:10 | 23     |
	| 5  | 3          | 2017-12-23 08:32:11 | 78     |
	| 6  | 3          | 2017-11-21 03:33:10 | 34     |

## Final Result

	| id | Product_id | created_at          | prices |
	|----|------------|---------------------|--------|
	| 1  | 1          | 2017-12-23 08:32:11 | 10     |
	| 3  | 2          | 2017-12-23 08:32:11 | 43     |
	| 5  | 3          | 2017-12-23 08:32:11 | 78     |

## Query

```
SELECT p.*,d.name FROM prices p
inner join product d 
on d.id=p.product_id
WHERE 
prices.id IN 
    ( SELECT MAX(prices.id) FROM prices GROUP BY prices.created_at ) 
```

### Source
[Stackoverflow](https://stackoverflow.com/questions/47951500/combine-latest-records-with-table)

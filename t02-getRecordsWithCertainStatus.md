# Status Quo

**Product JOINT with Revision Table:**

```
SELECT *
FROM product AS p
INNER JOIN revisions AS r ON p.revision_id = r.id 
ORDER BY p.id;
```
```
| id | name     | prices | revision_id | id | revision_status |
|----|----------|--------|-------------|----|-----------------|
| 1  | Produkt1 | 10     | 1           | 1  | 1               |
| 2  | Produkt1 | 4      | 2           | 2  | 0               |
| 3  | Produkt1 | 2      | 3           | 3  | null            |
| 4  | Product2 | 42     | 4           | 4  | 1               |
| 5  | Produkt2 | 43     | 5           | 5  | null            |
| 6  | Produkt2 | 78     | 6           | 6  | 0               |
| 7  | Produkt3 | 1      | 7           | 7  | 1               |
| 8  | Produkt3 | 3      | 8           | 8  | null            |
| 9  | Produkt3 | 4      | 9           | 9  | null            |
| 10 | Produkt4 | 33     | 10          | 10 | 1               |
```

# Final Result

	| id | name     | prices | revision_id | id | revision_status |
	|----|----------|--------|-------------|----|-----------------|
	| 1  | Produkt1 | 10     | 1           | 1  | 1               |
	| 3  | Produkt1 | 2      | 3           | 3  | null            |
	| 4  | Product2 | 42     | 4           | 4  | 1               |
	| 5  | Produkt2 | 43     | 5           | 5  | null            |
	| 7  | Produkt3 | 1      | 7           | 7  | 1               |
	| 8  | Produkt3 | 3      | 8           | 8  | null            |
	| 9  | Produkt3 | 4      | 9           | 9  | null            |
  
# Query  

```
SELECT * 
FROM products AS p 
INNER JOIN revisions AS r ON p.revisions_id = r.id 
WHERE p.name IN ( 
	SELECT p.name FROM products AS p 
	INNER JOIN revisions AS r ON p.revisions_id = r.id 
	GROUP BY p.name 
	HAVING COUNT(IFNULL(r.revision_status, 0)) > 1) 
ORDER BY p.name 
```

# Reference
* [Stackoverflow](https://stackoverflow.com/questions/48033029/getting-rows-which-have-a-certain-revision-status)
* [SQLFiddle](http://sqlfiddle.com/#!9/acb4d0/16/0)

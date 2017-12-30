# Status Quo

**Product Table:**

	| id | name      | prices | revision_id |
	|----|-----------|--------|-------------|
	| 1  | Produkt 1 | 10     | 1           |
	| 2  | Produkt 1 | 4      | 2           |
	| 3  | Produkt 1 | 2      | 3           |
	| 4  | Product 2 | 42     | 4           |
	| 5  | Produkt 2 | 43     | 5           |
	| 6  | Produkt 3 | 78     | 6           |


**Revisions Table:**

	| id | revision_status |
	|----|-----------------|
	| 1  | 1               |
	| 2  | 0               |
	| 3  | 0               |
	| 4  | 1               |
	| 5  | 0               |
	| 6  | 1               |	
	
# Final Result

	| id | name      | prices | revision_id | revision_status |
	|----|-----------|--------|-------------|-----------------|
	| 1  | Produkt 1 | 10     | 1           | 1               |
	| 2  | Produkt 1 | 4      | 2           | 0               |
	| 3  | Produkt 1 | 2      | 3           | 0               |
	| 4  | Product 2 | 42     | 4           | 1               |
	| 5  | Produkt 2 | 43     | 5           | 0               |
  
# Query  

```

```

# Reference
* [Stackoverflow](https://stackoverflow.com/questions/48033029/getting-rows-which-have-a-certain-revision-status)

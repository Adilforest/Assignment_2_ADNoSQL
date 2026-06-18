# Advanced Databases / NoSQL — Assignment 2 (AITU)

Intermediate MongoDB query practice: projection, sorting, pagination, regex text search, conditional filters on arrays, and multi-condition queries on a restaurant dataset.

![MongoDB](https://img.shields.io/badge/MongoDB-NoSQL-47A248?logo=mongodb) ![Shell](https://img.shields.io/badge/Shell-mongo-grey)

---

## Overview

**Dataset:** `restaurants.json` — a standard MongoDB sample dataset with restaurant records containing `name`, `borough`, `cuisine`, `address` (street, building, zipcode), and nested `grades` arrays (grade, score, date).

**Goal:** Write and execute ten progressively complex `find()` queries, demonstrating projection, multi-key sorting, skip/limit pagination, comparison operators, logical operators, regex matching, array element queries, and compound filters.

---

## What it covers

- **Projection** — returning only selected fields (`name`, `street`, `cuisine`, `borough`, `building`).
- **Sorting** — ascending and descending sort on string fields (`borough`, `cuisine`).
- **Pagination** — combining `.skip()` and `.limit()` for offset-based result windows.
- **Comparison filter** — `score $gte 35` on a numeric field inside nested grades.
- **Logical operators** — `$or` combining cuisine and borough conditions.
- **Regex text search** — `$regex` for name prefix (`^Ma`) and substring (`Man`) matching.
- **Array element query** — `grades.grade: "B"` to filter restaurants that received a specific grade at least once.
- **Multi-field compound filter** — `$in` on zipcode list combined with `$in` on cuisine list; dual sort.
- Results verified with screenshots in `images/`.

---

## Repository structure

```
Assignment_2_ADNoSQL/
├── restaurants.json     # Restaurant dataset (JSON array, ~3 800 documents)
├── mongoimport          # Import command reference
├── images/              # Screenshots of each query result (tasks 1–10)
└── README.md
```

---

## Getting started

```bash
# 1. Start MongoDB
mongod

# 2. Import the restaurant data
mongoimport --db mydb --collection rest \
  --file restaurants.json --jsonArray

# 3. Open the mongo shell
mongosh

# 4. Switch to your database and run queries
use mydb

# Example — Task 5: American cuisine or Bronx borough, skip 10, limit 15
db.rest.find(
  { $or: [ { cuisine: "American" }, { borough: "Bronx" } ] },
  { name: 1, "address.street": 1, _id: 0 }
).skip(10).limit(15)
```

---

Adil Ormanov — [GitHub](https://github.com/Adilforest)

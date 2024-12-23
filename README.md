# Assignment 1: Advanced Databases and NoSQL - MongoDB Queries

This project contains solutions for the MongoDB assignment. It includes completed queries, steps to import data into MongoDB, and screenshots of query outputs.

---

## Assignment Description

The tasks involve solving MongoDB queries for analyzing restaurant data. Each task's results are executed and verified in MongoDB shell.

- **Task 2**: Fetch the first 5 documents, displaying `name`, `street`, and `cuisine`, sorted by `cuisine` in descending order.
- **Task 3**: Fetch the first 15 documents, displaying `name`, `street`, and `borough`, sorted by `borough` in ascending order, skipping the first 3 documents.
- **Task 4**: Fetch the first 10 documents, displaying `name`, `street`, and `building` where `score` is greater than or equal to 35.
- **Task 5**: Fetch the first 15 documents, displaying the `name` and `street` where cuisine is "American" or borough is "Bronx", skipping the first 10 documents.
- **Task 6**: Fetch the first 10 documents, displaying `name`, `cuisine`, `borough`, where `name` starts with "Ma".
- **Task 7**: Fetch the first 10 documents, displaying `name`, `cuisine`, `borough`, where `name` contains "Man".
- **Task 8**: Fetch the first 10 documents, where `name` starts with "Ma" and has received a grade of "B" at least once.
- **Task 9**: Fetch the first 10 documents, where the `zipcode` is `10462`, `11374`, or `11219` and `cuisine` is "Pizza" or "Seafood". Display `cuisine` and `name`, sorting by `cuisine` in descending order.
- **Task 10**: Fetch the first 10 documents, where the `zipcode` is `10462`, `11374`, `11219` or `cuisine` is "Pizza", "Seafood", or "American". Display `cuisine` and `name`, sorted by `cuisine` in ascending order.

All queries are written and executed using the `db.collection.find()` method.

---

## How to Run the Project

1. **Import Data into MongoDB**:
   Use the following command to import the `restaurants.json` file into your MongoDB database:

   ```bash
   mongoimport --db <your_database> --collection rest --file restaurants.json --jsonArray
   ```

   Replace `<your_database>` with the database name of your choice.

2. **Run MongoDB Queries**:
   Open the MongoDB shell, connect to your database, and execute the queries for each task.

   For example:
   ```javascript
   db.rest.find(
       { $or: [ { cuisine: "American" }, { borough: "Bronx" } ] },
       { name: 1, "address.street": 1, _id: 0 }
   )
   .skip(10)
   .limit(15);
   ```

3. **Capture Outputs**:
   After running each query, take a screenshot of the output and save it in the `images/` directory with names corresponding to tasks (e.g., `task_1.png`, `task_2.png`, etc.).

---

## Files Included

1. **`restaurants.json`**:
   A JSON file containing the dataset of restaurants, including fields such as `name`, `address`, `cuisine`, `grades`, and more.

2. **`mongoimport`**:
   A placeholder for the shell command to import the dataset into MongoDB.

3. **`images/`**:
   A directory containing 11 screenshots (`task_1.png` to `task_10.png`) showcasing query outputs.

4. **`README.md`**:
   The project documentation file (this file).

---

## Example Query and Result

### Task 2 Query:
Fetch the first 5 documents, displaying `name`, `street`, and `cuisine`, sorted by `cuisine` in descending order.

```javascript
db.rest.find(
    {},
    { name: 1, "address.street": 1, cuisine: 1, _id: 0 }
)
.sort({ cuisine: -1 })
.limit(5);
```

### Sample Output:
```json
[
  { "name": "Restaurant A", "street": "Main Street", "cuisine": "Seafood" },
  { "name": "Restaurant B", "street": "Broadway", "cuisine": "Pizza" },
  { "name": "Restaurant C", "street": "Park Avenue", "cuisine": "Italian" },
  { "name": "Restaurant D", "street": "5th Avenue", "cuisine": "American" },
  { "name": "Restaurant E", "street": "High Street", "cuisine": "American" }
]
```

---

## Uploading Project to GitHub

1. Open a terminal and navigate to the project directory:
   ```bash
   cd Assignment_1_ADNoSQL
   ```

2. Initialize a Git repository and commit the files:
   ```bash
   git init
   git add .
   git commit -m "Initial commit for MongoDB assignment"
   ```

3. Link the repository to GitHub:
   ```bash
   git remote add origin <your_github_repo_url>
   git branch -M main
   git push -u origin main
   ```

Replace `<your_github_repo_url>` with your GitHub repository URL.

---

If you have any questions or issues, feel free to reach out!
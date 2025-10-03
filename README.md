# MongoDB scripts — how to run and include Compass screenshots

This repository contains sample MongoDB scripts used in the exercises: a shell-style script `queries.js` and a Node.js data loader `insert_books.js`.

This README explains how to run both, how to capture and add MongoDB Compass screenshots, and where to place them so they render in this README.

## Files of interest

- `queries.js` — MongoDB shell script (for `mongosh`) that creates the `books` collection, inserts sample documents, runs queries, aggregation pipelines, and creates indexes.
- `insert_books.js` — Node.js script that populates the `plp_bookstore` database using the official MongoDB Node driver.
- `screenshots/` — contains placeholder SVGs; replace them with real PNG screenshots named `compass-collection.png` and `compass-indexes.png` to show images in this README.

## A tiny contract

- Inputs: local MongoDB server (or Atlas connection), Node.js (to run `insert_books.js`).
- Outputs: populated `plp_bookstore.books` collection and optional README screenshots.
- Success: scripts complete without errors and screenshots render in README.

## Run `queries.js` with mongosh (quick)

1. Open PowerShell.
2. Start the MongoDB shell and connect to your server (default local):

```powershell
mongosh
```

3. In `mongosh`, run the script and create the sample data:

```javascript
use plp_bookstore
load('C:/Users/hp/OneDrive/Desktop/mongodb-data-layer-fundamentals-and-advanced-techniques-Marci-design/queries.js')
```

Notes:
- If you re-run the script you may get duplicate records. To start clean run `db.books.drop()` before `load()`.
- If your path differs, adjust the `load()` path accordingly.

## Run `insert_books.js` with Node.js

1. Ensure Node.js is installed. Check versions:

```powershell
node -v; npm -v
```

2. Install dependencies (repository already contains a `package.json` for examples):

```powershell
npm install
```

3. Run the script (adjust the connection URI inside `insert_books.js` if you use Atlas):

```powershell
node insert_books.js
```

The script drops the collection if it finds documents, then inserts the sample books and prints a summary.

## Add MongoDB Compass screenshots (so they render in this README)

1. Open MongoDB Compass and connect to the same server.
2. Navigate to `plp_bookstore` → `books` collection.
3. Take two screenshots you want to show in the README:
   - collection/documents view
   - Indexes tab view
4. Save them into the `screenshots/` folder with these exact filenames:
   - `screenshots/compass-collection.png`
   - `screenshots/compass-indexes.png`

If you don't provide PNGs, the README currently points to those filenames; the repo contains SVG placeholders named `compass-collection.svg` and `compass-indexes.svg` as backups.

### How to capture on Windows

- Use Snip & Sketch or Snipping Tool (Win+Shift+S) and save the image as PNG.
- Suggested size: ~1200x675 or any widescreen size for good display in GitHub README.

## Embedded screenshots (will show when PNGs are added)

![MongoDB Compass - Collection](screenshots/compass-collection.png)

![MongoDB Compass - Indexes](screenshots/compass-indexes.png)

## Cleanup commands (mongosh)

If you want to remove the sample data after testing, run:

```javascript
use plp_bookstore
db.books.drop()
```

To remove indexes created by the exercises:

```javascript
db.books.dropIndex('title_1')
db.books.dropIndex('author_1_published_year_-1')
```

## Troubleshooting

- "mongosh" not found: install MongoDB Server or MongoDB Shell from MongoDB website.
- Node connection errors: check connection string in `insert_books.js`.
- Permission/file path errors when using `load()` in `mongosh`: ensure the path is correct and readable.

## Next steps I can do for you

- If you upload your Compass screenshots here, I will add them to `screenshots/` and commit them so they render in the README.
- I can add an npm script to run `insert_books.js` (`npm run seed`) or create a small GitHub Action that warns if the PNG screenshots are missing on PRs.

---

If you want me to embed your actual screenshots now, upload `compass-collection.png` and `compass-indexes.png` and I'll add them to the repo and commit.# MongoDB Fundamentals - Week 1

## Setup Instructions

Before you begin this assignment, please make sure you have the following installed:

1. **MongoDB Community Edition** - [Installation Guide](https://www.mongodb.com/docs/manual/administration/install-community/)
2. **MongoDB Shell (mongosh)** - This is included with MongoDB Community Edition
3. **Node.js** - [Download here](https://nodejs.org/)

### Node.js Package Setup

Once you have Node.js installed, run the following commands in your assignment directory:

```bash
# Initialize a package.json file
npm init -y

# Install the MongoDB Node.js driver
npm install mongodb
```

## Assignment Overview

This week focuses on MongoDB fundamentals including:
- Creating and connecting to MongoDB databases
- CRUD operations (Create, Read, Update, Delete)
- MongoDB queries and filters
- Aggregation pipelines
- Indexing for performance

## Submission

Complete all the exercises in this assignment and push your code to GitHub using the provided GitHub Classroom link.

## Getting Started

1. Accept the GitHub Classroom assignment invitation
2. Clone your personal repository that was created by GitHub Classroom
3. Install MongoDB locally or set up a MongoDB Atlas account
4. Run the provided `insert_books.js` script to populate your database
5. Complete the tasks in the assignment document

## Files Included

- `Week1-Assignment.md`: Detailed assignment instructions
- `insert_books.js`: Script to populate your MongoDB database with sample book data

## Requirements

- Node.js (v18 or higher)
- MongoDB (local installation or Atlas account)
- MongoDB Shell (mongosh) or MongoDB Compass

## Resources

- [MongoDB Documentation](https://docs.mongodb.com/)
- [MongoDB University](https://university.mongodb.com/)
- [MongoDB Node.js Driver](https://mongodb.github.io/node-mongodb-native/) 

## Compass screenshots (embed)

Place your MongoDB Compass screenshots into the `screenshots/` folder and name them:

- `screenshots/compass-collection.png` (collection/documents view)
- `screenshots/compass-indexes.png` (Indexes tab view)

When those files exist the images will be displayed below. If you haven't added real screenshots yet, the repository contains SVG placeholders with similar names.

![MongoDB Compass - Collection](screenshots/compass-collection.png)

![MongoDB Compass - Indexes](screenshots/compass-indexes.png)

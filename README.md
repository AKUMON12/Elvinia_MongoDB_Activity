# Elvinia, Tristan Jesus V.
---

## markdown
# 📘 MongoDB Basics & Alternative Perspectives

## 🗄️ Sample MongoDB Operations

```
> use movieDB
< switched to db movieDB

> db.createCollection("movies")

> db.movies.insertMany([
  { title: "Inception", director: "Christopher Nolan", year: 2010, genre: "Sci-Fi", rating: 8.8 },
  { title: "The Matrix", director: "Lana Wachowski", year: 1999, genre: "Action", rating: 8.7 },
  { title: "Interstellar", director: "Christopher Nolan", year: 2014, genre: "Sci-Fi", rating: 8.6 }
])
< {
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6810bfdd2eb41aa0e53c36ae'),
    '1': ObjectId('6810bfdd2eb41aa0e53c36af'),
    '2': ObjectId('6810bfdd2eb41aa0e53c36b0')
  }
}

> db.movies.find();
> db.movies.find({ director: "Christopher Nolan" });
> db.movies.find({ rating: { $gt: 8.7 } });

> db.movies.updateOne(
    { title: "Interstellar" },
    { $set: { rating: 8.9 } }
);
> db.movies.deleteOne({ title: "The Matrix" });
< {
  acknowledged: true,
  deletedCount: 1
}

```

---

## 💬 Discussion Questions

### 1. How is the schema in MongoDB different from relational tables?

MongoDB offers a dynamic schema where documents in a collection can vary in field names and types. This flexibility is useful in real-world scenarios where data is not uniform.

Relational databases, on the other hand, enforce a static schema. Before inserting data, all fields and relationships must be predefined in tables, which promotes consistency but can slow down schema evolution.

**Illustrative Comparison:**
- **MongoDB:** You can add a `cast` array to one movie document without affecting others.
- **Relational:** You would need to create a separate `cast` table and set up foreign keys.

---

### 2. What are the pros and cons of flexible schemas?

Flexible schemas reduce the need for data migrations and allow developers to adapt data structures on the fly, which is great for startups or rapidly evolving projects. However, without structure, teams risk technical debt.

**Pros:**
- Accommodates evolving business requirements.
- Can store rich, hierarchical data natively (e.g., arrays, embedded objects).
- Low friction for onboarding new types of data.

**Cons:**
- Makes data validation and consistency the developer's responsibility.
- Difficult to ensure reporting tools and analytics get reliable fields.
- Schema-less doesn't mean structure-less—good design is still necessary.

---

### 3. When would you choose NoSQL over traditional SQL databases?

NoSQL is especially powerful in distributed environments and where high throughput or flexibility is more important than strict consistency. It's also preferred for storing user-generated content, logs, or document-heavy systems.

**You’d likely choose NoSQL when:**
- You’re building a product catalog where each item may have unique attributes.
- Your application needs to handle large volumes of real-time user interactions (e.g., chat apps, social feeds).
- You want to avoid rigid normalization and instead favor embedded relationships.

**SQL is better suited for:**
- Accounting systems or applications with many-to-many relationships.
- Scenarios where complex transactions and ACID guarantees are essential.
- Business intelligence platforms with structured reporting needs.

---


![image](https://github.com/user-attachments/assets/dc489405-dabe-47d9-a25b-39f5ea960cc3)

# 🧪 Interview Challenge: Building a Virtual Knowledge Graph (VKG)

## 🎯 Context

You are given multiple relational datasets stored in PostgreSQL.  
Each dataset represents a different domain (e.g., customers, cities, sports teams).

Your task is to design and implement a **Virtual Knowledge Graph (VKG)** using an **Ontology-Based Data Access (OBDA)** approach.

The goal is to provide a **unified semantic layer** over heterogeneous data sources without physically moving the data.

---

## 🧱 Available Data Sources

You can use the following publicly available PostgreSQL datasets:

### 1. 🎬 Pagila (DVD Rental Database)
- Link: https://neon.com/postgresql/postgresql-getting-started/postgresql-sample-database

👉 Description:
- Customers, rentals, films, stores  
- ~15–30 tables, rich relational structure  
- Widely used PostgreSQL sample DB  

---

### 2. 🌍 World Dataset (Geography)
- Download hub: https://wiki.postgresql.org/wiki/Sample_Databases  

👉 Tables:
- country
- city
- countrylanguage  

👉 Purpose:
- Provides a shared **location dimension** for linking datasets  

---

### 3. ⚽ SportDB (Sports Data)
- Website / samples: http://www.sportsdb.org/sd/samples  

👉 Tables:
- teams, players, matches  

👉 Purpose:
- Introduces **organizations and events**
- Can be linked to cities/countries  

---

### (Optional) 4. 🎵 Chinook (Media Store)
- Download: https://github.com/lerocha/chinook-database  

👉 Purpose:
- Alternative to Pagila (simpler schema)
- Good for smaller demos  

---

## 🚀 Tasks

### 1. Data Understanding
- Explore the schemas of the datasets
- Identify:
  - Primary keys
  - Foreign keys
  - Possible cross-dataset links (e.g., city names, country codes)

---

### 2. Ontology Design
Create a lightweight ontology (OWL or RDFS) that models:

- `Person`
- `City`
- `Country`
- `Organization` (e.g., team, store)
- `CreativeWork` (e.g., film)
- `Event` (optional)

Define:
- Classes
- Object properties (e.g., `livesIn`, `locatedIn`)
- Data properties (e.g., name, id)

---

### 3. Mapping (Core Task)
Define mappings from relational data to RDF using:
- R2RML or Ontop native mappings

Ensure:
- Each entity has a unique IRI
- Cross-dataset relationships are captured

Examples:
- `customer.address.city → City`
- `team.city → City`
- `customer → Person`, `player → Person`

---

### 4. VKG Setup
- Configure a VKG system (e.g., Ontop)
- Connect it to PostgreSQL
- Load:
  - Ontology
  - Mappings

---

### 5. Querying

Write SPARQL queries such as:

1. List all customers and the cities they live in  
2. Find all teams located in the same country as a given customer  
3. Retrieve all people (customers + players) grouped by country  
4. Combine at least 2 datasets in one query  

---

### 6. (Optional) Optimization & Reasoning
- Apply basic reasoning (RDFS / OWL 2 QL)
- Optimize mappings or queries
- Explain SPARQL → SQL rewriting

---

## 📦 Deliverables

- Ontology file (`.owl` or `.ttl`)
- Mapping file (`.ttl` or `.obda`)
- SQL setup scripts
- 3–5 SPARQL queries
- README including:
  - Design choices
  - Assumptions
  - Limitations

---

## ✅ Evaluation Criteria

| Area | What We Look For |
|------|-----------------|
| Modeling | Clear, consistent ontology |
| Integration | Ability to link datasets |
| Mappings | Correct OBDA mappings |
| Querying | Meaningful SPARQL queries |
| Understanding | VKG / OBDA explanation |
| Bonus | Performance, reasoning |

---

## 💡 Tips

- Keep the ontology simple  
- Focus on **semantic alignment across datasets**  
- Think in terms of **concepts, not tables**  

---

## 🧠 Key Concept

A Virtual Knowledge Graph exposes relational data as RDF and allows querying it with SPARQL, while queries are translated into SQL and executed on the original databases.

---

## ⏱️ Expected Time

- Take-home: 4–8 hours  
- Discussion: 60–90 minutes  

---

## 🏁 Bonus Challenge (Optional)

- Link to an external KG (e.g., DBpedia)
- Expose a SPARQL endpoint
- Add a simple visualization
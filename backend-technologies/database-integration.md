# Database Integration

- Database integration in Node.js involves connecting the application to a database to store, retrieve, and manage data. 
- This process is essential for creating dynamic applications that interact with data.

**1. Choosing a Database**

- SQL Databases: Such as PostgreSQL and MySQL, use structured query language (SQL) for defining and manipulating data.
- NoSQL Databases: Such as MongoDB and CouchDB, are designed for unstructured data and offer flexible schemas.

**2. Connecting to a Database**

For SQL Databases: Use libraries like pg for PostgreSQL or mysql2 for MySQL.

**3. Performing CRUD Operations**

- Create: Insert new data into the database
- Read: Query data from the database.
- Update: Modify existing data.
- Delete: Remove data from the database.

----

## MySQL Database Setup

To integrate a MySQL database with Node.js application, you need to configure a connection pool, handle queries, and ensure proper table creation.

### Setting Up the Database Connection

Use the `mysql2/promise` library to create a connection pool that allows efficient handling of multiple database connections.

Database Connection Configuration:

```js
import mysql from 'mysql2/promise';

const pool = mysql.createPool({
    host: process.env.DB_HOST,
    user: process.env.DB_USER,
    password: process.env.DB_PASSWORD,
    database: process.env.DB_NAME,
    connectionLimit: 10
});

console.log('MySQL Pool created successfully');

```

> mysql.createPool(): Creates a pool of connections to the MySQL database.
>
> connectionLimit: Specifies the maximum number of connections in the pool.

### Query Execution Utility

Create a utility function for executing SQL queries. This function handles acquiring and releasing connections automatically.

Query Execution Function:

```js
const query = async (sql, values) => {
    const connection = await pool.getConnection();
    try {
        const [results] = await connection.query(sql, values);
        return results;
    } catch (err) {
        return err;
    } finally {
        if (connection) {
            connection.release();
        }
    }
};

export default query;
```

> pool.getConnection(): Obtains a connection from the pool.
> 
> connection.query(): Executes the SQL query.
> 
> connection.release(): Releases the connection back to the pool.

### Recipe Controller Functions

Implement controller functions for managing recipe data. These functions interact with the database using the query utility.

Recipe Controller Example:

```js
import query from '../config/db.js';

const recipeControllers = {
    getAllRecipes: async (req, res) => {
        try {
            const sql = 'SELECT * FROM recipes';
            const recipes = await query(sql);
            res.status(200).json(recipes);
        } catch (error) {
            console.error('Error fetching recipes:', error);
            res.status(500).json({ error: 'Error fetching recipes' });
        }
    },

    getRecipeByID: async (req, res) => {
        const { id } = req.params;
        try {
            const sql = 'SELECT * FROM recipes WHERE id = ?';
            const recipe = await query(sql, [id]);
            if (recipe.length === 0) {
                res.status(404).json({ error: 'Recipe not found' });
            } else {
                res.status(200).json(recipe[0]);
            }
        } catch (error) {
            console.error('Error fetching recipe:', error);
            res.status(500).json({ error: 'Error fetching recipe' });
        }
    },

    getRecipesByName: async (req, res) => {
        const { q } = req.query;
        try {
            if (!q) {
                return await recipeControllers.getAllRecipes(req, res);
            }
            const sql = 'SELECT * FROM recipes WHERE name LIKE ?';
            const searchTerm = `%${q}%`;
            const recipes = await query(sql, [searchTerm]);
            if (recipes.length === 0) {
                res.status(404).json({ error: 'Recipe not found' });
            } else {
                res.status(200).json(recipes);
            }
        } catch (error) {
            console.error('Error fetching recipes by name:', error);
            res.status(500).json({ error: 'Error fetching recipes by name' });
        }
    },

    postRecipe: async (req, res) => {
        const { name, description } = req.body;
        try {
            if (!name) {
                return res.status(400).json({ error: 'Name of the recipe is required' });
            }
            const sql = 'INSERT INTO recipes (name, description) VALUES(?, ?)';
            const values = [name, description || null];
            const result = await query(sql, values);
            const insertedRecipeId = result.insertId;
            const fetchSql = 'SELECT * FROM recipes WHERE id = ?';
            const newRecipe = await query(fetchSql, [insertedRecipeId]);
            res.status(201).json({
                recipe: newRecipe[0],
                message: `"${newRecipe[0].name}" Recipe is added successfully`,
                result: result
            });
        } catch (error) {
            console.error('Error adding recipe:', error);
            res.status(500).json({ error: 'Error adding recipe' });
        }
    },

    updateRecipe: async (req, res) => {
        const { id } = req.params;
        const { name, description } = req.body;
        try {
            if (!name && !description) {
                return res.status(400).json({ error: 'At least one field (name or description) is required to update' });
            }
            let sql = 'UPDATE recipes SET ';
            const values = [];
            if (name) {
                sql += 'name = ?, ';
                values.push(name);
            }
            if (description) {
                sql += 'description = ?, ';
                values.push(description);
            }
            sql = sql.slice(0, -2);
            sql += ' WHERE id = ?';
            values.push(id);
            const result = await query(sql, values);
            if (result.affectedRows === 0) {
                return res.status(404).json({ error: 'Recipe not found' });
            }
            const fetchSql = 'SELECT * FROM recipes WHERE id = ?';
            const updatedRecipe = await query(fetchSql, [id]);
            res.status(200).json({ recipe: updatedRecipe[0], message: 'Recipe updated successfully', result: result });
        } catch (error) {
            console.error('Error updating recipe:', error);
            res.status(500).json({ error: 'Error updating recipe' });
        }
    },

    deleteRecipe: async (req, res) => {
        const { id } = req.params;
        try {
            const sql = 'SELECT * FROM recipes WHERE id = ?';
            const selectRecipe = await query(sql, [id]);
            if (selectRecipe.length === 0) {
                return res.status(404).json({ error: 'Recipe not found' });
            }
            const deleteSql = 'DELETE FROM recipes WHERE id = ?';
            const result = await query(deleteSql, [id]);
            res.status(200).json({ message: `"${selectRecipe[0].name}" is deleted successfully`, recipeId: id, result: result });
        } catch (error) {
            console.error('Error deleting recipe:', error);
            res.status(500).json({ error: 'Error deleting recipe' });
        }
    }
};

export default recipeControllers;
```

### Table Creation Script

Create the necessary database table using a script that ensures the table is created if it doesn’t already exist.

Table Creation Script:

```js
import query from '../config/db.js';

const createRecipeTable = async () => {
    const sql = `
        CREATE TABLE IF NOT EXISTS recipes (
            id INT AUTO_INCREMENT PRIMARY KEY,
            name VARCHAR(255) NOT NULL,
            description TEXT,
            created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
            updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
        )
    `;

    try {
        await query(sql);
    } catch (error) {
        console.error('Error creating recipes table:', error);
    }
};

export default createRecipeTable;
```

> Table Definition:
> 
> **id:** Auto-increment primary key.
>
> **name:** Non-nullable field for the recipe name
> 
> **description:** Optional field for additional details.
> 
> **created_at & updated_at:** Timestamps for record creation and last update.
>

This section demonstrates how to integrate MySQL with a Node.js application by configuring a connection pool, executing queries, and managing recipe data.
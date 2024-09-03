Certainly! Here’s an updated version of the `.md` file that includes all relevant information regarding `node-pg-migrate`, its usage, and additional details you might find useful.

---

# PostgreSQL Migration Notes with `node-pg-migrate`

This document provides a comprehensive record of migrations applied to a PostgreSQL database using `node-pg-migrate`. It includes detailed explanations of how `node-pg-migrate` is used, how to create and manage migrations, and notes on each migration.

## Table of Contents

1. [Introduction to `node-pg-migrate`](#introduction-to-node-pg-migrate)
2. [Migration Overview](#migration-overview)
3. [Creating Migrations](#creating-migrations)
4. [Migration Details](#migration-details)
   - [Migration 1: `<migration-name>`](#migration-1-migration-name)
   - [Migration 2: `<migration-name>`](#migration-2-migration-name)
   - ...
5. [Rollback Instructions](#rollback-instructions)
6. [Best Practices](#best-practices)
7. [Additional Resources](#additional-resources)

---

## Introduction to `node-pg-migrate`

`node-pg-migrate` is a migration tool for PostgreSQL that allows you to manage database schema changes in a version-controlled way. It provides a framework to create and execute migrations that alter the database schema over time.

### Key Features

- **Declarative Migrations:** Write migrations in JavaScript or TypeScript.
- **Version Control:** Track schema changes in a version-controlled manner.
- **Rollback Support:** Easily revert changes with rollback functions.
- **Automatic Migration Detection:** Detect and apply pending migrations.

### Installation

To install `node-pg-migrate`, run:

```bash
npm install node-pg-migrate
```

### Configuration

Configure `node-pg-migrate` by adding a `node-pg-migrate` section to your `package.json` or by creating a `node-pg-migrate.config.js` file. Basic configuration options include the database connection settings and migration directories.

```json
// Example configuration in package.json
"node-pg-migrate": {
  "dir": "migrations",
  "databaseUrl": "postgres://username:password@localhost:5432/mydatabase"
}
```

## Migration Overview

This section outlines the general purpose and goals for the migrations applied to the database. Migrations may include creating tables, modifying columns, adding indexes, or seeding initial data.

## Creating Migrations

To create a new migration, use the `create` command provided by `node-pg-migrate`. 

```bash
npx node-pg-migrate create migration-name
```

This command generates a new migration file with the current timestamp and a name you provide. You can then edit this file to define the changes you want to apply to the database.

### Migration File Structure

A migration file typically contains two main functions:

- **`up(pgm)`**: Defines the changes to be applied to the database schema.
- **`down(pgm)`**: Defines how to revert the changes made in the `up` function.

Example of a migration file:

```javascript
exports.shorthands = undefined;

exports.up = (pgm) => {
  pgm.createTable('users', {
    id: 'id',
    name: { type: 'varchar(100)', notNull: true },
    created_at: { type: 'timestamp', default: pgm.func('current_timestamp') }
  });
  pgm.createIndex('users', 'name');
};

exports.down = (pgm) => {
  pgm.dropTable('users');
};
```

## Migration Details

### Migration 1: `<migration-name>.js`

- **File Name:** `<migration-name>.js`
- **Date Created:** `YYYY-MM-DD`
- **Author:** `<Your Name>`
- **Description:** A brief summary of what this migration accomplishes.

#### Changes Made

1. **Table Created/Modified:** 
    - **Table Name:** `table_name`
    - **Description:** Details of the table creation or modification. For example, "Created a new table to store user data."

2. **Columns Added/Removed/Modified:**
    - **Column Name:** `column_name`
    - **Change:** Specify what was done (e.g., added a new column, changed data type from `INTEGER` to `VARCHAR`).
    - **Description:** Explanation of why the change was made.

3. **Indexes Created/Removed:**
    - **Index Name:** `index_name`
    - **Change:** Created or removed.
    - **Description:** Explain the purpose of the index.

4. **Constraints Added/Removed:**
    - **Constraint Name:** `constraint_name`
    - **Change:** Added or removed.
    - **Description:** Describe what the constraint enforces or why it was removed.

5. **Data Seeded:**
    - **Table Name:** `table_name`
    - **Data:** Describe any initial data inserted or modified during the migration.

#### Rollback Instructions

- **Rollback Code:**
  - Describe the steps or provide code to revert the migration. Typically involves the `down` function in `node-pg-migrate`.

  ```javascript
  // Example rollback code snippet
  exports.down = (pgm) => {
      pgm.dropTable('table_name');
  };
  ```

#### Notes

- **Additional Information:**
  - Any extra details relevant to this migration, such as dependencies on other migrations, potential issues, or special instructions.

### Migration 2: `<migration-name>.js`

- **File Name:** `<migration-name>.js`
- **Date Created:** `YYYY-MM-DD`
- **Author:** `<Your Name>`
- **Description:** A brief summary of what this migration accomplishes.

#### Changes Made

1. **Table Created/Modified:** 
    - **Table Name:** `table_name`
    - **Description:** Details of the table creation or modification.

2. **Columns Added/Removed/Modified:**
    - **Column Name:** `column_name`
    - **Change:** Specify what was done.
    - **Description:** Explanation of why the change was made.

3. **Indexes Created/Removed:**
    - **Index Name:** `index_name`
    - **Change:** Created or removed.
    - **Description:** Purpose of the index.

4. **Constraints Added/Removed:**
    - **Constraint Name:** `constraint_name`
    - **Change:** Added or removed.
    - **Description:** What the constraint enforces or why it was removed.

5. **Data Seeded:**
    - **Table Name:** `table_name`
    - **Data:** Describe any data seeded or modified.

#### Rollback Instructions

- **Rollback Code:**
  - Describe or provide code to revert the migration.

  ```javascript
  // Example rollback code snippet
  exports.down = (pgm) => {
      pgm.dropTable('table_name');
  };
  ```

#### Notes

- **Additional Information:**
  - Any extra details relevant to this migration.

---

## Best Practices

1. **Test Migrations Locally:**
   - Always test migrations in a local or staging environment before applying them to production.

2. **Keep Migrations Small:**
   - Aim for small, focused migrations. This makes it easier to troubleshoot and rollback if necessary.

3. **Document Changes Clearly:**
   - Provide clear and concise explanations for each change. This helps others understand the purpose and impact of the migration.

4. **Provide Rollback Instructions:**
   - Always include a rollback function to revert the migration if something goes wrong.

5. **Use Meaningful File Names:**
   - Name migration files descriptively to reflect the changes they apply.

6. **Handle Dependencies:**
   - Ensure that migrations are applied in the correct order, especially if they depend on each other.

---

## Additional Resources

- [node-pg-migrate Documentation](https://github.com/salsita/node-pg-migrate)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [Node.js Documentation](https://nodejs.org/en/docs/)

---

By maintaining this document, you ensure that the database schema changes are well-documented and organized, making it easier to manage and understand the evolution of your database over time.

---

Feel free to modify this template as needed to fit your specific use case and project requirements!

# Manual command for run migration
`DATABASE_URL=postgres://tusharnagdive@localhost:5432/social_network_mig npm run migrate up`



# Albert1025
intro to SQL

sqlite> CREATE TABLE users (
   ...> id INTEGER PRIMARY KEY AUTOINCREMENT,
   ...> first_name VARCHAR(64) NOT NULL,
   ...> last_name VARCHAR(64) NOT NULL,
   ...> email VARCHAR(128) UNIQUE NOT NULL,
   ...> created_at DATETIME NOT NULL,
   ...> updated_at DATETIME NOT NULL
   ...> );
sqlite> 
sqlite> .table
users
sqlite> .schema
CREATE TABLE users (
id INTEGER PRIMARY KEY AUTOINCREMENT,
first_name VARCHAR(64) NOT NULL,
last_name VARCHAR(64) NOT NULL,
email VARCHAR(128) UNIQUE NOT NULL,
created_at DATETIME NOT NULL,
updated_at DATETIME NOT NULL
);
sqlite> INSERT INTO users
   ...> (first_name, last_name, email, created_at, updated_at)
   ...> VALUES
   ...> ('Chan Hon', 'Tan', 'tch_albert@hotmail.com', DATETIME('now'), 
   ...> DATETIME('now'));
sqlite> SELECT * FROM users;
1|Chan Hon|Tan|tch_albert@hotmail.com|2018-03-16 08:32:19|2018-03-16 08:32:19
sqlite> INSERT INTO users
   ...> (first_name, last_name, email, created_at, updated_at)
   ...> VALUES
   ...> ('Joshua', 'Teng', 'jedicoder@example.com', DATETIME('now'), DATETIME('now'));
sqlite> SELECT * FROM users
   ...> ;
1|Chan Hon|Tan|tch_albert@hotmail.com|2018-03-16 08:32:19|2018-03-16 08:32:19
2|Joshua|Teng|jedicoder@example.com|2018-03-16 08:32:58|2018-03-16 08:32:58
sqlite> INSERT INTO users
   ...> (first_name, last_name, email, created_at, updated_at)
   ...> VALUES
   ...> ('Joshua', 'Teng', 'jedicoder@example.com', DATETIME('now'), DATETIME('now'));
Error: UNIQUE constraint failed: users.email
sqlite> SELECT * FROM users;
1|Chan Hon|Tan|tch_albert@hotmail.com|2018-03-16 08:32:19|2018-03-16 08:32:19
2|Joshua|Teng|jedicoder@example.com|2018-03-16 08:32:58|2018-03-16 08:32:58
sqlite> ALTER TABLE users ADD nickname VARCHAR(64) NOT NULL
   ...> ;
Error: Cannot add a NOT NULL column with default value NULL
sqlite> ALTER TABLE users ADD nickname VARCHAR(64) NOT NULL;
Error: Cannot add a NOT NULL column with default value NULL
sqlite> ALTER TABLE users ADD VARCHAR(64) nickname NOT NULL;
Error: near "(": syntax error
sqlite> ALTER TALBE users ADD COLUMN nickname NOT NULL;
Error: near "TALBE": syntax error
sqlite> ALTER TABLE users ADD COLUMN nickname NOT NULL;
Error: Cannot add a NOT NULL column with default value NULL
sqlite> SELECT * FROM users;
1|Chan Hon|Tan|tch_albert@hotmail.com|2018-03-16 08:32:19|2018-03-16 08:32:19
2|Joshua|Teng|jedicoder@example.com|2018-03-16 08:32:58|2018-03-16 08:32:58
sqlite> ALTER TABLE users ADD COLUMN nickname TEXT;
sqlite> .schema users
CREATE TABLE users (
id INTEGER PRIMARY KEY AUTOINCREMENT,
first_name VARCHAR(64) NOT NULL,
last_name VARCHAR(64) NOT NULL,
email VARCHAR(128) UNIQUE NOT NULL,
created_at DATETIME NOT NULL,
updated_at DATETIME NOT NULL
, nickname TEXT);
sqlite> UPDATE users SET nickname='pookie butt' WHERE id=2
   ...> ;
sqlite> SELECT * FROM users;
1|Chan Hon|Tan|tch_albert@hotmail.com|2018-03-16 08:32:19|2018-03-16 08:32:19|
2|Joshua|Teng|jedicoder@example.com|2018-03-16 08:32:58|2018-03-16 08:32:58|pookie butt
sqlite> UPDATE users SET first_name='Josh'AND SET nickname='NinjaCoder' WHERE id=2;
Error: near "SET": syntax error
sqlite> UPDATE users SET first_name='Josh' WHERE id=2;
sqlite> UPDATE users SET nickname='NinjaCoder' WHERE id=2;
sqlite> SELECT * FROM users;
1|Chan Hon|Tan|tch_albert@hotmail.com|2018-03-16 08:32:19|2018-03-16 08:32:19|
2|Josh|Teng|jedicoder@example.com|2018-03-16 08:32:58|2018-03-16 08:32:58|NinjaCoder

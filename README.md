# FirstDatabaseSQLlite
(base) C:\Users\User\Desktop\Back end\Day 7 SQL>sqlite3 dummy.db
SQLite version 3.26.0 2018-12-01 12:34:55
Enter ".help" for usage hints.
sqlite> CREATE TABLE users (
   ...>   id INTEGER PRIMARY KEY AUTOINCREMENT,
   ...>   first_name VARCHAR(64) NOT NULL,
   ...>   last_name VARCHAR(64) NOT NULL,
   ...>   email VARCHAR(128) UNIQUE NOT NULL,
   ...>   created_at DATETIME NOT NULL,
   ...>   updated_at DATETIME NOT NULL
   ...> );
sqlite> INSERT INTO users
   ...> (first_name, last_name, email, created_at, updated_at)
   ...> VALUES
   ...> ('Joshua', 'Teng', 'jedicoder@example.com', DATETIME('now'), DATETIME('now'));
sqlite> SELECT * FROM users
   ...> ;
1|Joshua|Teng|jedicoder@example.com|2019-02-14 03:33:27|2019-02-14 03:33:27
sqlite> INSERT INTO users
   ...> (first_name, last_name, email, created_at, updated_at)
   ...> VALUES
   ...> ('Claudia', 'Chia', 'happygirlcoder@example.com', DATETIME('now'), DATETIME('now'));
sqlite> SELECT * FROM users
   ...> ;
1|Joshua|Teng|jedicoder@example.com|2019-02-14 03:33:27|2019-02-14 03:33:27
2|Claudia|Chia|happygirlcoder@example.com|2019-02-14 03:34:26|2019-02-14 03:34:26
sqlite> INSERT INTO users
   ...> (first_name, last_name, email, created_at, updated_at)
   ...> VALUES
   ...> ('Joshua', 'Teng', 'jedicoder@example.com', DATETIME('now'), DATETIME('now'));
Error: UNIQUE constraint failed: users.email
sqlite> INSERT INTO users
   ...> (first_name, last_name, email, created_at, updated_at)
   ...> VALUES
   ...> ('Joshua', 'Teng', 'jedicoder2@example.com', DATETIME('now'), DATETIME('now'));
sqlite> SELECT * FROM users
   ...> ;
1|Joshua|Teng|jedicoder@example.com|2019-02-14 03:33:27|2019-02-14 03:33:27
2|Claudia|Chia|happygirlcoder@example.com|2019-02-14 03:34:26|2019-02-14 03:34:26
3|Joshua|Teng|jedicoder2@example.com|2019-02-14 03:36:22|2019-02-14 03:36:22
sqlite> ALTER TABLE users ADD COLUMN nickname VARCHAR(64);
sqlite> .schema users
CREATE TABLE users (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  first_name VARCHAR(64) NOT NULL,
  last_name VARCHAR(64) NOT NULL,
  email VARCHAR(128) UNIQUE NOT NULL,
  created_at DATETIME NOT NULL,
  updated_at DATETIME NOT NULL
, nickname VARCHAR(64));
sqlite> UPDATE users SET nickname = 'pookie butt' WHERE id=1 OR id=3;
sqlite> SELECT * FROM users
   ...> ;
1|Joshua|Teng|jedicoder@example.com|2019-02-14 03:33:27|2019-02-14 03:33:27|pookie butt
2|Claudia|Chia|happygirlcoder@example.com|2019-02-14 03:34:26|2019-02-14 03:34:26|
3|Joshua|Teng|jedicoder2@example.com|2019-02-14 03:36:22|2019-02-14 03:36:22|pookie butt
sqlite> UPDATE users SET first_name = 'Josh' WHERE id=1 OR id=3;
sqlite> UPDATE users SET updated_at = DATETIME('now') WHERE id=1 OR id=3;
sqlite> SELECT * FROM users
   ...> ;
1|Josh|Teng|jedicoder@example.com|2019-02-14 03:33:27|2019-02-14 03:40:20|pookie butt
2|Claudia|Chia|happygirlcoder@example.com|2019-02-14 03:34:26|2019-02-14 03:34:26|
3|Josh|Teng|jedicoder2@example.com|2019-02-14 03:36:22|2019-02-14 03:40:20|pookie butt
sqlite>


# Database Creation

## E-LEARN Database

### Table: institution

```sql
CREATE DATABASE e_learn_portal;
```

This SQL code creates a database named `e_learn_portal`.

### Table: institution

```sql
CREATE TABLE institution (
    institution_id INT AUTO_INCREMENT,
    name VARCHAR(255),
    created_at TIMESTAMP,
    isactive VARCHAR(255),
    superadminpin VARCHAR(255),
    adminpin VARCHAR(255),
    email VARCHAR(255),
    PRIMARY KEY (institution_id)
);
```

This SQL code creates a table named `institution` with various fields such as `institution_id`, `name`, `created_at`, `isactive`, `superadminpin`, `adminpin`, and `email`. The `institution_id` is set as the primary key.

### Table: e_student

```sql
CREATE TABLE e_student (
    s_id INT AUTO_INCREMENT,
    email VARCHAR(255),
    name VARCHAR(255),
    password VARCHAR(255),
    learn INT,
    gender VARCHAR(255),
    profilePic VARCHAR(255),
    timestamp TIMESTAMP,
    isactive VARCHAR(255),
    institution_id INT,
    PRIMARY KEY (s_id),
    FOREIGN KEY (institution_id) REFERENCES institution(institution_id)
);
```

This SQL code creates a table named `e_student` with fields like `s_id`, `email`, `name`, `password`, `learn`, `gender`, `profilePic`, `timestamp`, `isactive`, and `institution_id`. The `s_id` is set as the primary key, and there is a foreign key reference to the `institution` table.

### Table: e_admininfo

```sql
CREATE TABLE e_admininfo (
    a_id INT AUTO_INCREMENT,
    name VARCHAR(255),
    email VARCHAR(255),
    password VARCHAR(255),
    created_at TIMESTAMP,
    institution_id INT,
    isactive VARCHAR(255),
    PRIMARY KEY (a_id),
    FOREIGN KEY (institution_id) REFERENCES institution(institution_id)
);
```

This SQL code creates a table named `e_admininfo` with fields such as `a_id`, `name`, `email`, `password`, `created_at`, `institution_id`, and `isactive`. The `a_id` is set as the primary key, and there is a foreign key reference to the `institution` table.

### Table: learningresources

```sql
CREATE TABLE learningresources (
    lr_id INT AUTO_INCREMENT,
    a_id INT,
    opened INT,
    totalremarks INT,
    rsctitle VARCHAR(255),
    learndefinition LONGTEXT,
    route VARCHAR(255),
    created_at TIMESTAMP,
    isactive VARCHAR(255),
    institution_id INT,
    PRIMARY KEY (lr_id),
    FOREIGN KEY (a_id) REFERENCES e_admininfo(a_id),
    FOREIGN KEY (institution_id) REFERENCES institution(institution_id)
);
```

This SQL code creates a table named `learningresources` with fields like `lr_id`, `a_id`, `opened`, `totalremarks`, `rsctitle`, `learndefinition`, `route`, `created_at`, `isactive`, and `institution_id`. The `lr_id` is set as the primary key, and there are foreign key references to the `e_admininfo` and `institution` tables.

### Table: chatroom

```sql
CREATE TABLE chatroom (
    c_id INT AUTO_INCREMENT,
    s_id INT,
    a_id INT,
    tutor VARCHAR(255),
    chat LONGTEXT,
    created_at TIMESTAMP,
    isactive VARCHAR(255),
    institution_id INT,
    PRIMARY KEY (c_id),
    FOREIGN KEY (s_id) REFERENCES e_student(s_id),
    FOREIGN KEY (a_id) REFERENCES e_admininfo(a_id),
    FOREIGN KEY (institution_id) REFERENCES institution(institution_id)
);
```

This SQL code creates a table named `chatroom` with fields like `c_id`, `s_id`, `a_id`, `tutor`, `chat`, `created_at`, `isactive`, and `institution_id`. The `c_id` is set as the primary key, and there are foreign key references to the `e_student`, `e_admininfo`, and `institution` tables.

### Table: remarks_table

```sql
CREATE TABLE remarks_table (
    r_id INT AUTO_INCREMENT,
    lr_id INT,
    s_id INT,
    remark LONGTEXT,
    created_at TIMESTAMP,
    isactive VARCHAR(255),
    institution_id INT,
    PRIMARY KEY (r_id),
    FOREIGN KEY (lr_id) REFERENCES learningresources(lr_id),
    FOREIGN KEY (s_id) REFERENCES e_student(s_id),
    FOREIGN KEY (institution_id) REFERENCES institution(institution_id)
);
```

This SQL code creates a table named `remarks_table` with fields like `r_id`, `lr_id`, `s_id`, `remark`, `created_at`, `isactive`, and `institution_id`. The `r_id` is set as the primary key, and there are foreign key references to the `learningresources`, `e_student`, and `institution` tables.

### Table: message

```sql
CREATE TABLE message (
    messageid INT AUTO_INCREMENT,
    name VARCHAR(255),
    email VARCHAR(255),
    created_at TIMESTAMP,
    message LONGTEXT,
    PRIMARY KEY (messageid)
);
```

This SQL code creates a table named `message`.


## Generation of sample data for tables e_student and e_admininfo

- [Random Student SQL Query](https://enshikuku.github.io/random_student_SQLquery/)
- [Random Admin SQL Query](https://enshikuku.github.io/random_student_SQLquery/admin.html)

# USEA

## Database

Using Mysql

1. **Users table**:
   - This table will store information about the users.
   - Attributes: `user_id` (Primary Key), `username`, `password`, etc.

2. **Prayer Times table**:
   - This table will store information about the prayer times for each user.
   - Attributes: `prayer_time_id` (Primary Key), `user_id` (Foreign Key referencing Users table), `prayer_name` (e.g., Fajr, Dhuhr, Asr, Maghrib, Isha), `time`, `date`, etc.

3. **Errors table**:
   - This table will store information about any errors encountered during prayer time notifications.
   - Attributes: `error_id` (Primary Key), `user_id` (Foreign Key referencing Users table), `error_message`, `timestamp`, etc.

```sql
-- usea.users definition

CREATE TABLE `users` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `username` varchar(100) NOT NULL,
  `password` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `users_unique` (`username`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- usea.prayer_times definition

-- usea.prayer_times definition

CREATE TABLE `prayer_times` (
  `prayer_time_id` int(11) NOT NULL AUTO_INCREMENT,
  `user_id` int(11) DEFAULT NULL,
  `code_zone` varchar(100) DEFAULT NULL,
  `prayer_name` varchar(100) DEFAULT NULL,
  `prayer_time` varchar(100) DEFAULT NULL,
  `create_date` timestamp NULL DEFAULT current_timestamp(),
  PRIMARY KEY (`prayer_time_id`),
  KEY `prayer_times_users_FK` (`user_id`),
  CONSTRAINT `prayer_times_users_FK` FOREIGN KEY (`user_id`) REFERENCES `users` (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=113 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
-- usea.errors definition

CREATE TABLE `errors` (
  `error_id` int(11) NOT NULL AUTO_INCREMENT,
  `user_id` int(11) DEFAULT NULL,
  `error_message` varchar(100) DEFAULT NULL,
  `create_date` timestamp NULL DEFAULT current_timestamp(),
  PRIMARY KEY (`error_id`),
  KEY `errors_users_FK` (`user_id`),
  CONSTRAINT `errors_users_FK` FOREIGN KEY (`user_id`) REFERENCES `users` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
```

## Technology

### Programming Code

- PHP
- HTML
- SQL

### Library

- getID3
- PHPMailer

### Future Improvement

- Configuration created separately
- Proper login
- Separated between HTML and PHP
- Created Microservices

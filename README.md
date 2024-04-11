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

getID3 is a PHP library used for retrieving information about audio and video files. It provides a wide range of functionality for analyzing multimedia files and extracting metadata from them. 

Here are some advantages of using getID3 in PHP:

1. **Support for Various File Formats**: getID3 supports a wide range of audio and video file formats, including MP3, Ogg Vorbis, FLAC, WAV, MPEG-4, AVI, and many others. This makes it suitable for analyzing and extracting metadata from different types of multimedia files.

2. **Comprehensive Metadata Extraction**: getID3 can extract a wide range of metadata from multimedia files, including information such as file duration, bitrate, codec information, sample rate, track title, artist, album, genre, and more. This metadata can be useful for categorizing and organizing multimedia files in applications.

3. **Ease of Use**: getID3 is relatively easy to use in PHP applications. It provides simple and intuitive APIs for accessing file metadata, making it straightforward to integrate into PHP projects.

4. **Customizable**: getID3 is highly customizable and extensible. It allows developers to configure various options and settings according to their requirements. Additionally, developers can extend its functionality by adding custom plugins or modifying existing ones.

5. **Active Development and Community Support**: getID3 is actively maintained and has a supportive community of developers. Updates and improvements are regularly released, ensuring compatibility with the latest multimedia file formats and standards.

6. **Cross-Platform Compatibility**: getID3 is compatible with different operating systems and web servers that support PHP, making it suitable for use in a variety of environments.

Overall, getID3 is a versatile and powerful tool for working with multimedia files in PHP applications, providing developers with the means to extract detailed metadata and analyze various aspects of audio and video content.

- PHPMailer

PHPMailer is a popular email-sending library for PHP, offering several advantages for developers when compared to using PHP's built-in `mail()` function or other email libraries. Here are some advantages of using PHPMailer:

1. **Simplicity and Ease of Use**: PHPMailer provides a simple and intuitive API for sending emails, making it easy for developers to integrate email functionality into their PHP applications.

2. **Support for Multiple Mail Transfer Methods**: PHPMailer supports various email transfer methods, including SMTP, sendmail, and mail(), allowing developers to choose the most suitable method for their environment.

3. **SMTP Authentication**: PHPMailer supports SMTP authentication, allowing you to send emails through authenticated SMTP servers. This is essential for sending emails through third-party email services like Gmail, Outlook, or Mailgun, which often require authentication.

4. **Attachments and Embedded Images**: PHPMailer allows you to easily attach files and embed images in your emails. This is useful for sending files, images, or HTML emails with inline images.

5. **HTML and Plain Text Emails**: PHPMailer supports both HTML and plain text email formats, giving you the flexibility to send emails in the format that best suits your needs.

6. **Character Encoding and Language Support**: PHPMailer handles character encoding and language issues automatically, ensuring that emails are delivered correctly, even when sending emails in different languages or character sets.

7. **Error Handling and Debugging**: PHPMailer provides robust error handling and debugging capabilities, making it easier to diagnose and fix issues with email delivery.

8. **Security Features**: PHPMailer includes security features to help prevent email abuse, such as SMTP authentication, secure SMTP connections (SSL/TLS), and built-in support for SMTP over SSL (SMTPS).

9. **Active Development and Community Support**: PHPMailer is actively maintained and has a large community of users and developers who contribute to its development and provide support. This ensures that PHPMailer stays up-to-date with the latest email standards and security practices.

Overall, PHPMailer is a versatile and reliable library for sending emails in PHP applications, offering a range of features and benefits that make it a popular choice among developers.

### Future Improvement

- Configuration created separately
- Proper login
- Separated between HTML and PHP
- Created Microservices

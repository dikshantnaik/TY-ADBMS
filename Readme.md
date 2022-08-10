# How to use

- All the Database Procedure and Funtions Query is Here with
- And all the code that i used in Frontend to use this is in [utils.java](https://github.com/dikshantnaik/TY-ADBMS/blob/main/util.java)
  File So you can also Refer that ..How i Called the Funtions from backend and used that in my Existing Code!
- The [utils.java](https://github.com/dikshantnaik/TY-ADBMS/blob/main/util.java) is a Part of the code of my Entire Project
- The Query was Automaticaly Generated using PhpMyAdmin
  You can do it follow below Steps

## Resource

- My Databased used [jsp-project](https://github.com/dikshantnaik/TY-ADBMS/blob/main/jsp-project.sql)
  You can Import This to your PhpmyAdmin and see it working
- My Code where i Called all Funtions and procedure using Java : [utils.java](https://github.com/dikshantnaik/TY-ADBMS/blob/main/util.java)

### How to use PhpMyAdmin to Generate Procedure and Funtions

- Open PhpMyAdmin(Not gonno say how)
- At Right-hand side Selct your Database For eg."[jsp-project](https://github.com/dikshantnaik/TY-ADBMS/blob/main/jsp-project.sql)"
- In the Upper-Right Corner You'll see <i>"Routines"</i> Tab <br> <i>\*After you Select a DataBase </i>

  ![WhatsApp Image 2022-08-10 at 3 56 28 PM](https://user-images.githubusercontent.com/45972990/183879407-162033c5-9cba-46dc-aaf8-230ac5b4bddb.jpeg)


- After That Just Click <i> 'Create new Routine' </i> at Upper Right Corner a Pop screen will appear
- Enter Procedure/Funtion name. Select type if Funtion or not . Add required Parameters
- Write your main Logic in Defination tab and Done ..Just Click GO

Sample ScreenShot Attached
![image](https://user-images.githubusercontent.com/45972990/183879689-7949f48e-2273-4206-b641-c3befcbd6bb5.png)

# Mysql Procedures and Funtion Query used in My Project

Its Exported from phpMyadmin

## Register Procedure

```sql
CREATE DEFINER=`root`@`localhost` PROCEDURE `Register`
(IN `susername` VARCHAR(50), IN `sname` VARCHAR(50),
IN `scourse` VARCHAR(50), IN `spassword` VARCHAR(500))
INSERT INTO students
VALUES(NULL,susername,sname,scourse,spassword)
```

## Login Funtion

```sql
CREATE DEFINER=`root`@`localhost` FUNCTION `login`
(`susername` VARCHAR(50), `spassword` VARCHAR(50)) RETURNS int(1)
RETURN(EXISTS(SELECT * FROM students
WHERE students.username = susername
AND students.username = spassword))$$
```

## InsertReview

```sql
CREATE DEFINER=`root`@`localhost` PROCEDURE `InsertReviews`
(IN `course_id` INT, IN `susername` VARCHAR(50),
IN `sreview` VARCHAR(100))
INSERT INTO review VALUES(NULL,course_id,(SELECT studentid
FROM students
WHERE username = susername),NULL,sreview)$$
```

## Remove ItemFromCart

```sql
CREATE DEFINER=`root`@`localhost`
PROCEDURE `removeItemFromCart`(IN `susername` VARCHAR(50),
IN `c_id` INT)
DELETE FROM cart
WHERE sid = (SELECT studentid from students WHERE username=susername)
and  cid= c_id$$
```

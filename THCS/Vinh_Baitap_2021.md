# Bài 1:
# ĐỀ: ![image](https://user-images.githubusercontent.com/79911792/110800652-e6b37700-82d8-11eb-9ed6-e674328c013c.png)
# Code:
```
var n:int64;
f1,f2:text;
function kt(n:int64):boolean;
var s:string;
i:longint;
begin
str(n,s);
for i:=1 to length(s) do
if s[i]<>'0' then
if n mod (ord(s[i])-48)<>0 then exit(false);
exit(true);
end;
begin
assign(f1,'NUM.INP'); reset(f1);
assign(f2,'NUM.OUT'); rewrite(f2);
readln(f1,n);
n:=n-1;
repeat
inc(n);
until kt(n);
write(f2,n);
close(f1);
close(f2);
end.
```
# Link: https://ideone.com/AgmokN

# Bài 2:
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110801012-4c076800-82d9-11eb-9b48-c4a7fc7ecf01.png)
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110801321-9be62f00-82d9-11eb-9430-4d0aa15b4a7b.png)
# Code:
```
var s:string;
f1,f2:text;
function kt1(s:string):boolean;
var a,b,c,d,code,i:byte;
begin
for i:=1 to length(s)-3 do
begin
val(s[i],a,code);
val(s[i+1],b,code);
val(s[i+2],c,code);
val(s[i+3],d,code);
if (a+1=b)and(b+1=c)and(c+1=d) then exit(true);
end;
exit(false);
end;
function kt2(s:string):boolean;
var i:byte;
begin
for i:=1 to length(s)-2 do
if (s[i]=s[i+1])and(s[i+1]=s[i+2]) then exit(true);
exit(false);
end;
function kt3(s:string):boolean;
var i,d:byte;
begin
d:=0;
for i:=1 to length(s)-1 do
begin
if s[i]=s[i+1] then inc(d);
if d=2 then exit(true);
end;
exit(false);
end;
function kt4(s:string):boolean;
var d:array['0'..'9'] of longint;
i:byte;
begin
fillchar(d,sizeof(d),0);
for i:=1 to length(s) do
begin
inc(d[s[i]]);
if d[s[i]]=5 then exit(true);
end;
exit(false);
end;
begin
assign(f1,'PHONE.INP'); reset(f1);
assign(f2,'PHONE.OUT'); rewrite(f2);
readln(f1,s);
if (kt1(s))or(kt2(s))or(kt3(s))or(kt4(s)) then
begin write(f2,'YES'); close(f2); exit; end;
write(f2,'NO');
close(f1);
close(f2);
end.
```
# Link: https://ideone.com/VZZZvh

# Bài 3:
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110803018-401ca580-82db-11eb-917a-7371d5cd3a44.png)
# Code:
```
var h,m,h1,m1:longint;
f1,f2:text;
t:int64;
begin
assign(f1,'CLOCK.INP'); reset(f1);
assign(f2,'CLOCK.OUT'); rewrite(f2);
readln(f1,h,m,h1,m1);
if (h=0)and(m=0) then t:=12;
m:=m-1;
repeat
inc(m);
if m=30 then inc(t) else
if m=60 then
begin
m:=0;
h:=h+1;
if h<=12 then t:=t+h else
if h>12 then t:=t+h-12;
end else
if m=0 then
begin
if h<=12 then t:=t+h else
if h>12 then t:=t+h-12;
end;
until (h=h1)and(m=m1);
write(f2,t);
close(f1);
close(f2);
end.
```
# Link: https://ideone.com/4JKYKk

# Bài 4:
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110804261-7e669480-82dc-11eb-8986-c8715c4ae72c.png)
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110804318-8f170a80-82dc-11eb-9070-7236b6b88070.png)
# Code:
```
var s,x:string;
n,t,i:longint;
f1,f2:text;
function kt(s,x:string):boolean;
var i:longint;
begin
for i:=1 to length(x) do
if pos(x[i],s)=0 then exit(false);
exit(true);
end;
begin
assign(f1,'CIPHER.INP'); reset(f1);
assign(f2,'CIPHER.OUT'); rewrite(f2);
readln(f1,s);
readln(f1,n);
for i:=1 to n do
begin
readln(f1,x);
if kt(s,x) then inc(t);
end;
write(f2,t);
close(f1);
close(f2);
end.
```
# Link: https://ideone.com/E50Gb4

# Bài 5:
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110805222-60e5fa80-82dd-11eb-8d0a-0e48982c6b52.png)
# Code:
```
var s,a,b:string;
f1,f2:text;
i,a1,b1,code,c:longint;
begin
assign(f1,'SUM.INP'); reset(f1);
assign(f2,'SUM.OUT'); rewrite(f2);
readln(f1,s);
a:=copy(s,1,pos(' ',s)-1);
b:=copy(s,pos(' ',s)+1,length(s)-pos(' ',s)+1);
s:='';
while length(a)<>length(b) do
if length(a)>length(b) then b:='0'+b else a:='0'+a;
for i:=length(a) downto 1 do
begin
val(a[i],a1,code);
val(b[i],b1,code);
c:=a1+b1;
s:=chr(c mod 10+48)+s;
end;
write(f2,s);
close(f1);
close(f2);
end.
```
# Link: https://ideone.com/yF6KZ7


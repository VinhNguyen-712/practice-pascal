# Bài 1: NUM
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110884208-3b8ad800-8341-11eb-94fb-db8edd138198.png)
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
# Link: https://ideone.com/92asNt

# Bài 2: PHONE
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110884303-66752c00-8341-11eb-8581-fc111c9d962a.png)
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110884330-6ffe9400-8341-11eb-8930-b9e0393e720d.png)
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
# Link: https://ideone.com/OjVDIv

# Bài 3: CLOCK
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110884432-991f2480-8341-11eb-8dfc-bd1581ef31c3.png)
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
# Link: https://ideone.com/yWXIZy

# Bài 4: CIPHER
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110884556-c23fb500-8341-11eb-8520-327b528f57d4.png)
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110884587-ccfa4a00-8341-11eb-902a-565d2dabc681.png)
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
# Link: https://ideone.com/AWPZt5

# Bài 5: SUM
# Đề: ![image](https://user-images.githubusercontent.com/79911792/110884686-f6b37100-8341-11eb-8db1-eb3f0c995b80.png)
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
# Link: https://ideone.com/RkRZzw

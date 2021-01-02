# **competitive-programming-setup**

1. Install sublime text editor
2. run the following command to install gcc compile

```
sudo apt-get update
sudo apt-get install build-essential\Open sublime text and do the following steps.
```

3. goto tools > build system > new build system and paste below code and save as c++14.sublime-build

``` sublime_build
{
"shell_cmd": "g++ -std=c++14 \"${file}\" -o \"${file_path}/${file_base_name}\" && \"${file_path}/${file_base_name}\"",

    "file_regex": "^(..[^:]_):([0-9]+):?([0-9]+)?:? (._)$",
    "working_dir": "${file_path}",
    "selector": "source.c, source.c++",
    "variants":
    [

{
"name": "Run",
"shell_cmd": "g++ -std=c++14 \"${file}\" -o \"${file_path}/${file_base_name}\" && \"${file_path}/${file_base_name}\""
}
]
}
```

4. tools > command pallet > search for package controller : install package and add it to sublime.
5. search and install the package sublimeAStyleFormatter (optional)
6. Go to preferences > browse packages > sublimeAStyleFormatter > SublimeAStyleFormatter.sublime-settings and change "autoformat\_on\_save":true (optional)
7. create a direactory /opt/cp and create "template" inside cp directory. (for windows do in C://cp)
8. create 3 files main.cpp input.txt and outpot.txt inside template directory and copy your template inside main.cpp

<br>
```
#include<bits/stdc++.h>
using namespace std;

struct hash\_pair {
template \<class T1, class T2>
size\_t operator()(const pair\<T1, T2>& p) const
{
auto hash1 = hash{}(p.first);

auto hash2 = hash{}(p.second);

return hash1 ^ hash2;
}
};

void solve()
{
}

int main()
{

#ifndef ONLINE\_JUDGE
freopen("input.txt", "r", stdin);
freopen("output.txt", "w", stdout);
#endif


int t;
cin >> t;
while (t--)
{
    solve();
}
return 0;


}
```

1. add read permission to the template folder and all files inside it
2. go to preference > settings on sublime text editor add below two line at the end of the user settings

```
    "hot_exit":false,
    "remember\_open\_files": false
```

1. add shell script/batch file for respective flatform inside earlier created cp directory (filename cp\_start.sh/cp\_start.bat)

batch file code for windows

```
@echo off
set src\_folder=c:\template\cp
set dst\_folder=%1
if "%\~1"=="" goto done
xcopy %src\_folder% %dst\_folder% /E /H /C /I >NUL
cd %dst\_folder%
subl main.cpp input.txt output.txt
:done
```

shell script for mac and linux

```
#!/bin/bash

function cp_start() {
cp -R /opt/cp/template $1
subl $1/main.cpp $1/input.txt $1/output.txt
}
```

1. (linux/mac) add "source /opt/cp/cp\_start.sh" at end of the \~/.bashrc or \~/.zshrc file and run "source \~.bashrc" after complition
2. (windows) add the cp folder to the path
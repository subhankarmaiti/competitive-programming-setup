# competitive-programming-setup

## Linux (Debian Based)

Install sublime text editor and
Do the following steps.

- tools > build system > new build system

  ```sublime_build
  {
  "shell_cmd": "g++ -std=c++14 \"${file}\" -o \"${file_path}/${file_base_name}\" && \"${file_path}/${file_base_name}\"",
  "file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
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

- tools > install package sublimeAStyleFormatter
- tools > command pallet > search for package controller
- Go to preferences > browse packages > sublimeAStyleFormatter > SublimeAStyleFormatter.sublime-settings and change "autoformat_on_save":true

copy all the template folder to /opt/xyz

go to preference > settings
add below two line at the end of the user settings
"hot_exit":false,
"remember_open_files": false

Easy​Clang​Complete

batch file code for windows

```
@echo off
set src_folder=c:\template\cp
set dst_folder=%1
if "%~1"=="" goto done
xcopy %src_folder% %dst_folder% /E /H /C /I >NUL
cd %dst_folder%
subl main.cpp input.txt output.txt
:done
```

shell script for mac and linux

```
#!/bin/bash
# prints the input
function cp_start() {
  cp -R /opt/competitive-programming/template $1
  subl $1/main.cpp $1/input.txt $1/output.txt
}
```

very basic template

```
#include<bits/stdc++.h>
using namespace std;

struct hash_pair {
    template <class T1, class T2>
    size_t operator()(const pair<T1, T2>& p) const
    {
        auto hash1 = hash<T1>{}(p.first);
        auto hash2 = hash<T2>{}(p.second);
        return hash1 ^ hash2;
    }
};

void solve()
{
}

int main()
{

#ifndef ONLINE_JUDGE
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

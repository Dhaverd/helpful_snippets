# Copy files or do smth as another user in CMD/Powershell

```cmd
net use x: "\\shared\destination\" /user:domain\user password

:: Copy or do whay you need
copy "source destination" "\\shared\destination\target"

net use x: /d
```
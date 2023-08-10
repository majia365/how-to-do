
MacOS mas uninstall error "Not installed"
============================================


问题：app 通过mas 安装，但不能卸载。例如，

```
% mas list
937984704   Amphetamine  (5.2.2)

% mas uninstall 937984704
Error: Not installed
```

处理过程：

查看app信息，

```
% ll /Applications 
total 0
drwxr-xr-x  3 root   wheel  96  7 30 01:28 Amphetamine.app
```

猜测是用户权限问题，修改权限

```
 % sudo chown -R $(id -un):$(id -gn) /Applications/Amphetamine.app
```

处理结果，

```
% mas uninstall 937984704
Warning: Apps installed from the Mac App Store require root permission to remove.
==> App moved to trash: /Users/doctorx/.Trash/Amphetamine.app

% mas list
No installed apps found
```

OK.

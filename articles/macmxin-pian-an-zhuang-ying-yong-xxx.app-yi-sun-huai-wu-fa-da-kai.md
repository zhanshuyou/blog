# 12.Mac M芯片安装应用: xxx.app 已损坏，无法打开

开启 【任何来源】 选项

```sh
sudo spctl --master-disable
```

绕过签名及公证

```sh
# replace appName to your app
sudo xattr -rd com.apple.quarantine /Applications/{appName}.app
```

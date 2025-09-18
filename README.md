# flutter-setup-troubleshooting

🛠️ **Flutter 环境配置常见问题 & 解决方案（Windows 篇）**  
记录我在 Windows 上配置 Flutter 时踩过的坑和解决方案，希望能帮到后来人。

---

## 目录

1. [flutter 命令找不到](#1-flutter-命令找不到)
2. [PowerShell not found](#2-powershell-not-found)
3. [WHERE 命令找不到](#3-where-命令找不到)
4. [Git 未配置](#4-git-未配置)
5. [VS Code 提示 SDK 路径错误](#5-vs-code-提示-sdk-路径错误)
6. [运行项目时报错：No pubspec.yaml](#6-运行项目时报错no-pubspecyaml)

---

## 1. <span id="1-flutter-命令找不到"></span> `flutter` 命令找不到

**错误提示：**
```
flutter : 无法将“flutter”项识别为 cmdlet、函数、脚本文件或可运行程序的名称
```

**解决方法：**
- 确认 Path 中添加的是 `...\flutter\bin`，而不是其他路径。
- 修改环境变量后必须 **重启 PowerShell / VS Code**。

---

## 2. <span id="2-powershell-not-found"></span> PowerShell not found

**错误提示：**
```
Error: PowerShell executable not found. Either pwsh.exe or PowerShell.exe must be in your PATH.
```

**解决方法：**
- 在系统 Path 中添加：
  ```
  C:\Windows\System32\WindowsPowerShell\v1.0\
  ```
- 验证是否生效：
  ```
  where powershell
  ```

---

## 3. <span id="3-where-命令找不到"></span> WHERE 命令找不到

**错误提示：**
```
'WHERE' 不是内部或外部命令
```

**解决方法：**
- 在系统 Path 中添加以下路径：
  ```
  C:\Windows\System32
  C:\Windows
  C:\Windows\System32\Wbem
  ```

---

## 4. <span id="4-git-未配置"></span> Git 未配置

**错误提示：**
```
Error: Unable to find git in your PATH.
```

**解决方法：**
- 安装 [Git for Windows](https://git-scm.com/download/win)  
- 或手动在 Path 中添加：
  ```
  C:\Program Files\Git\mingw64\bin
  C:\Program Files\Git\cmd
  ```
- 验证 Git 是否安装：
  ```
  git --version
  ```

---

## 5. <span id="5-vs-code-提示-sdk-路径错误"></span> VS Code 提示 SDK 路径错误

**错误提示：**
```
The SDK configured in dart.flutterSdkPath is not a valid SDK folder
```

**解决方法：**
- 在 VS Code 设置中搜索 `flutter sdk path`
- 修改为实际 SDK 目录，例如：
  ```
  C:\Users\你的用户名\flutter_windows_3.35.4-stable\flutter
  ```

---

## 6. <span id="6-运行项目时报错no-pubspecyaml"></span> 运行项目时报错：No pubspec.yaml

**错误提示：**
```
Error: No pubspec.yaml file found.
This command should be run from the root of your Flutter project.
```

**解决方法：**
- 必须在项目根目录（有 `pubspec.yaml` 的地方）运行命令，例如：
  ```powershell
  cd C:\dev\flutter202509\ex03_hello
  flutter run -d chrome
  ```

---

> **建议：**
>
> - 每次修改环境变量后，务必**重启终端或 VS Code**。
> - 遇到环境问题时，优先用 `flutter doctor` 检查提示。
> - 多用 `where` 命令定位可执行文件路径。

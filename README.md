# Github-operations

## 基础篇

检查连接
```
ssh -T git@github.com
```
<br>
下载仓库东西

```
git clone https://github.com/username/repository.git
```
<br>

```
echo "# file_system" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:AallRight/file_system.git
git push -u origin main
```

---

生成新的 SSH 密钥对用于 Git 连接的步骤如下。这通常在你需要新的 SSH 密钥（例如更换旧的密钥、在不同的设备上使用或更新密钥）时执行。以下是详细步骤：

### 1. **生成新的 SSH 密钥对**

1. **打开终端**（Linux/macOS）或 **Git Bash**（Windows）。

2. **使用 `ssh-keygen` 生成新的密钥对**:
   ```bash
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```
   - **`-t rsa`**: 指定密钥类型为 RSA。
   - **`-b 4096`**: 指定密钥长度为 4096 位（更安全）。
   - **`-C "your_email@example.com"`**: 添加一个注释（通常是你的电子邮件地址），用于标识这个密钥。

3. **选择文件保存位置**:
   终端会提示你输入文件名以保存密钥。默认是 `~/.ssh/id_rsa`（Linux/macOS）或 `C:\Users\your_user\.ssh\id_rsa`（Windows）。如果你想保存为其他文件名，可以输入不同的路径，或者直接按 `Enter` 使用默认设置。

4. **设置密码**（可选）:
   你将被提示输入密码。这个密码将保护你的私钥。也可以留空以不使用密码，但不推荐。

   ```bash
   Enter passphrase (empty for no passphrase):
   Enter same passphrase again:
   ```

   密码可以增加额外的安全性，但每次使用密钥时需要输入。

### 2. **添加 SSH 密钥到 SSH 代理**

1. **启动 SSH 代理**（如果未启动）:
   ```bash
   eval "$(ssh-agent -s)"
   ```

2. **添加你的 SSH 私钥到代理**:
   ```bash
   ssh-add ~/.ssh/id_rsa
   ```

   如果你选择了其他文件名或路径，请用实际的文件路径替换 `~/.ssh/id_rsa`。

### 3. **将公钥添加到 GitHub**

1. **复制公钥内容**:
   使用以下命令将公钥内容复制到剪贴板：
   ```bash
   cat ~/.ssh/id_rsa.pub
   ```
   或者，如果你使用 macOS，可以使用：
   ```bash
   pbcopy < ~/.ssh/id_rsa.pub
   ```
   对于 Windows 用户，使用 Git Bash：
   ```bash
   clip < ~/.ssh/id_rsa.pub
   ```

2. **登录到 GitHub**:
   - 打开 GitHub 网站并登录你的账户。

3. **进入 SSH 密钥设置**:
   - 访问 [GitHub SSH 和 GPG 密钥设置页面](https://github.com/settings/keys)。
   - 点击 "New SSH key" 按钮。

4. **添加新的 SSH 密钥**:
   - 在 "Title" 字段输入一个名称来标识这个密钥（例如 "My Laptop"）。
   - 在 "Key" 字段粘贴你刚才复制的公钥内容。
   - 点击 "Add SSH key" 按钮保存密钥。

### 4. **测试 SSH 连接**

确保你的新 SSH 密钥配置正确，测试与 GitHub 的连接：

```bash
ssh -T git@github.com
```

如果配置正确，你会看到类似下面的输出：

```bash
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

### 总结

1. **生成新的 SSH 密钥对**:
   ```bash
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```

2. **添加密钥到 SSH 代理**:
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa
   ```

3. **将公钥添加到 GitHub**:
   - 复制公钥内容，并在 GitHub 设置页面添加新的 SSH 密钥。

4. **测试 SSH 连接**:
   ```bash
   ssh -T git@github.com
   ```

这样，你就可以生成新的 SSH 密钥并将其用于 GitHub 的身份验证。如果遇到任何问题或需要进一步帮助，请告诉我！

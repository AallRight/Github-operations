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


## 给fork配置远程库

查看远程状态

```
git remote -v
```
确定一个将被同步给 fork 远程的上游仓库：
```
git remote add upstream https://github.com/farmer-liuz1024/javastudy.git
```

再次查看状态确认是否配置成功。<br/>

## 同步fork

从上游仓库 fetch 分支和提交点，提交给本地 master，并会被存储在一个本地分支

```
git fetch upstream
```
切换到本地主分支：
```
git checkout master
```
把 upstream/master 分支合并到本地 master 上

```
git merge upstream/master
```

如果想更新到 GitHub 的 fork 上，直接

```
git push origin master
```



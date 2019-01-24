### git使用

阮一峰http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html

1.关联远程仓库`git remote add origin [远端仓库地址] `    如：git remote add origin  http://kb-webide

2.创建分支

```javascript
// 创建本地分支
1. 'git branch -b [分支名]'    // 创建分支并停留在当前分支
2. 'git checkout -b [分支名]'  // 创建分支并切换到该分支，区别于上面的命令
3. 'git push origin [分支名]'  // 将本地分支提交到远程仓库   即在远程仓库创建分支
```

3.查看分支

```javascript
// 列出分支名
1. git branch				 // 列出本地分支
2. git branch -r			 // 列出远程分支
3. git branch -a			 // 列出本地和远程分支
```

4.切换分支

```javascript
// 切换到其他分支
1. git checkout [分支名]	   // 切换到指定分支
2. git checkout -			 // 切换到上个分支	
```

5.恢复暂存区文件到工作区 `git checkout .`   等于是撤销操作           

6.删除分支
```javascript
1. git branch -d [分支名]		            // 删除本地分支
2. git push origin --delete [分支名]		// 删除远程分支
3. git branch -dr [remote/branch]
```
7.删除github文件夹

```javascript
1. git rm -r --cached [文件夹名]            // --cached不会删除本地的对应文件
2. git commit -m "delete files"			   // 提交删除操作
3. git push origin [分支名]				 
```


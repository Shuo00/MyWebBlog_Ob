只需要通过`git remote add <refs> <addr>`即可关联多个仓库  
refs 指向远程仓库, 默认的就是origin, addr 就是仓库地址了,比如`git@git.coding.net:mbinary/netease-cached-music.git`

输入  
`git remote add origin git@git.coding.net:mbinary/netease-cached-music.git`  
报错

> fatal: remote origin already exists.

这是远程仓库的refs相同的原因, 可以换个名字, 比如cod  
`git remote add cod git@git.coding.net:mbinary/netease-cached-music.git`  
即可,然后就关联上了多个仓库, 可以通过git remote -v 查看,

建立仓库，添加公钥（write）

使用`git push <refs> <branch>`多次
refs 远端名 branch分支
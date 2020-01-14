# github-batch-delete
快速清理github项目

# repolist.txt
> 注意格式，一行一个项目，由 用户名称/项目名称


# {token}
> 需要去github(https://github.com/settings/tokens) 申请 delete_repo 权限
> 然后替换下面的 {token}

# linux
```sh
while read r;
  do 
    curl -XDELETE -H 'Authorization: token {token}' "https://api.github.com/repos/$r ";
done < repos
```

# windows powershell
```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
get-content D:\repolist.txt | ForEach-Object { Invoke-WebRequest -Uri https://api.github.com/repos/$_ -Method “DELETE” -Headers @{"Authorization"="token {token}"} }
```

# 转载
https://juejin.im/post/5c42e2e76fb9a049ba41e06a

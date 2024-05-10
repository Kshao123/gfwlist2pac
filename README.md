# gfwlist2pac
Automatically convert gfwlist to pac everyday

Just use https://raw.githubusercontent.com/Kshao123/gfwlist2pac/master/gfwlist.pac

Proxys / CDNs:

- jsDelivr: https://cdn.jsdelivr.net/gh/Kshao123/gfwlist2pac@master/gfwlist.pac
- FastGit: https://raw.fastgit.org/Kshao123/gfwlist2pac/master/gfwlist.pac
- GitHub Proxy: https://ghproxy.com/https://github.com/Kshao123/gfwlist2pac/blob/master/gfwlist.pac
- 7ED SERVICE: https://raw.sevencdn.com/Kshao123/gfwlist2pac/master/gfwlist.pac

# Usage
#### 使用需知
> `PAC` 文件目前通过 [genpac](https://github.com/Kshao123/genpac) 和 [gfwlist](https://github.com/gfwlist/gfwlist) 生成，默认代理使用 `clash` 的 `127.0.0.1:7890`，如需修改参考如下
```diff
# file => .github/workfolws/update.yml
- genpac --pac-proxy "SOCKS5 127.0.0.1:7890; SOCKS 127.0.0.1:7890; DIRECT;" --gfwlist-url - --gfwlist-local gfwlist/gfwlist.txt -o gfwlist.pac --user-rule-from user-rules.txt
+ genpac --pac-proxy "你的代理 DIRECT;" --gfwlist-url - --gfwlist-local gfwlist/gfwlist.txt -o gfwlist.pac --user-rule-from user-rules.txt
```

# 自定义 pac rules
> fork 后可在 `user-rules.txt` 内根据规则（[http://adblockplus.org](http://adblockplus.org/en/filters)，或 [genpac](https://github.com/Kshao123/genpac)）添加白名单和Proxy名单

> 自定义规则会优先处理，覆盖 [gfwlist](https://github.com/gfwlist/gfwlist)（如需修改可参考上述需知），合理配置 `rules` 可提升速度
#### E.g
```shell
# file => user-rules.txt
!proxy
||baidu.com
*.taobao.com

!no proxy
@@||google.com
@@||openai.com
```
# 更新
> 如 `fork` 之后需要更新，需要开启 `Actions` 功能，默认每天更新，或 `push` 后
```yml
on:
  push:
    branches:
      - master
  # 更新时间 每日 19:37
  schedule:
    - cron: '37 19 * * *'
```

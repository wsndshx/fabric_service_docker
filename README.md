# 基于魔法的奇妙ELF(?)世界

>该项目所使用的服务端为Fabric, 并且以植物魔法为核心玩法.

![/637416773599398779 (2)](image/一个图片.png)

在一个普通的早上你醒过来后抬头看见的是一片陌生的天空(不对, 一般来说是看不见天空的), 你迷惑的坐了起来, 却惊恐的发现了一个更加恐怖的情况: 你的身体变成了精灵?

在短暂的混乱之后, 你慢慢明白了, 你现在似乎身处一个具有精灵与魔法的奇幻世界. 不知为何你来到了这个世界当中, 并且自身的种族变为了精灵族.

在经过一段时间的摸索后, 你发现虽然变成了精灵, 但也就身体的外貌发生了改变, 并不会受到精灵族一些习惯的影响, 例如你依然可以伐木, 吃肉等, 你的射箭技术也没得到突飞猛进的提高......

## mod列表

### 功能/玩法性mod

- [Fabric API - 大多数MOD的前置](https://www.mcmod.cn/class/3124.html) `服务端` `客户端`

- [帕秋莉手册的前置(Trinkets)](https://www.mcmod.cn/class/3985.html) `服务端` `客户端`

    - [帕秋莉手册(Patchouli)](https://www.mcmod.cn/class/1388.html) `服务端` `客户端`

        - [植物魔法(Botania)](https://www.mcmod.cn/class/332.html) `服务端` `客户端`

- [墓碑(Universal Graves)](https://www.mcmod.cn/class/5082.html) `服务端`

- [野营物品(Campanion)](https://www.mcmod.cn/class/2852.html) `服务端` `客户端`

- [伐树(FallingTree) - 更好的砍树体验](https://www.modrinth.com/mod/fallingtree) `服务端` `客户端`

- [季节(Fabric Seasons)](https://www.modrinth.com/mod/fabric-seasons) `服务端` `客户端`

- [烹饪(Culinaire)](https://www.mcmod.cn/class/2943.html) `服务端` `客户端`

### 性能优化mod

- [氪(Krypton) - 网络堆栈优化](https://www.modrinth.com/mod/krypton) `服务端` `客户端`

- [锂(Lithium) - 优化运行效率](https://www.modrinth.com/mod/lithium) `服务端`

- [内存优化(FerriteCore)](https://modrinth.com/mod/ferrite-core) `服务端` `客户端`

- [星光(Starlight) - 重写了光照引擎](https://github.com/PaperMC/Starlight) `服务端`

- [C^2M 引擎(C2ME) - 优化区块的性能](https://www.mcmod.cn/class/3511.html) `服务端`

- [钠(Sodium) - 客户端渲染优化](https://github.com/CaffeineMC/sodium-fabric) `客户端`

    - [钠 · 扩展(Sodium Extra)](https://www.modrinth.com/mod/sodium-extra) `客户端`

    - [铟(Indium) - 修复兼容性](https://www.mcmod.cn/class/3413.html) `客户端`

- [DFU载入优化(LazyDFU)](https://www.mcmod.cn/class/3407.html) `客户端`

- [服务器区块缓存的前置(Cloth Config API)](https://www.mcmod.cn/class/2346.html) `客户端`

    - [服务器区块缓存(Bobby)](https://www.mcmod.cn/class/5291.html) `客户端`

### 管理辅助

- [TabTPS - 查看服务器的性能数据](https://www.mcmod.cn/class/4089.html) `服务端`

- [LuckPerms - 权限管理](https://www.mcmod.cn/class/5192.html) `服务端`

- [Ledger - 方块记录](https://www.mcmod.cn/class/5389.html) `服务端`

    >Ledger由于会大量占用磁盘IOPS, 因此并未加入到列表当中, 有需要的可以自行解除注释

### 美化/实用mod

- [3D皮肤层(Skin Layers 3D)](https://www.mcmod.cn/class/4618.html) `客户端`

- [模组菜单(Mod Menu)](https://www.mcmod.cn/class/1675.html) `客户端`

- [Lambda的动态光源(LambDynamicLights)](https://www.mcmod.cn/class/2954.html) `客户端`

- [录像回放(Replay Mod)](https://www.mcmod.cn/class/1203.html) `客户端`

- [Lambda 的控制优化(LambdaControls)](https://www.mcmod.cn/class/5453.html) `客户端`

- [万用皮肤补丁 (CustomSkinLoader)](https://www.mcmod.cn/class/883.html) `客户端`

- [截图到剪贴板 (Screenshot to Clipboard)](https://www.mcmod.cn/class/2733.html) `客户端`

## 服务端部署方法

>需要服务端安装Docker

```bash
curl 'https://raw.githubusercontent.com/wsndshx/fabric_service_docker/master/Fabric_server_docker.yml' -o Fabric_server_docker.yml
curl 'https://raw.githubusercontent.com/wsndshx/fabric_service_docker/master/server_mod_list.txt' -o server_mod_list.txt
```

>如果MOD下载速度过慢, 可以使用添加了CDN的MOD列表文件: [server_mod_list_cdn.txt](https://raw.fastgit.org/wsndshx/fabric_service_docker/master/server_mod_list_cdn.txt); 
>
>记得把`server_mod_list_cdn.txt`改成`server_mod_list.txt`;

下载[docker配置文件](https://raw.githubusercontent.com/wsndshx/fabric_service_docker/master/Fabric_server_docker.yml)与[服务器MOD列表](https://raw.githubusercontent.com/wsndshx/fabric_service_docker/master/server_mod_list.txt)到任意一个目录, 并修改下列数据:

- 将第11行的`/Fabric_Service-data`修改为你想将服务器文件保存到的路径;

- 14, 15行根据实际需要进行修改;

- 17行若不想开启正版验证则取消注释;

修改完成后, 便可启动镜像: 
```bash
docker-compose -f Fabric_server_docker.yml up -d
```

## 权限配置

在容器运行起来后, 执行下述命令让特定用户取得管理权限(仅可控制权限插件)

```bash
# 授权插件的管理权
docker exec Fabric_Service_Mod rcon-cli lp user [玩家用户名] permission set luckperms.* true
# 授权游戏服务器管理权
docker exec Fabric_Service_Mod rcon-cli op [玩家用户名]
```

### TabTPS

需要玩家拥有tabtps.defaultdisplay权限才能使用, 下面用于为玩家的默认权限组赋予tabtps.defaultdisplay权限
```bash
docker exec Fabric_Service_Mod rcon-cli lp group default permission set tabtps.defaultdisplay true
```

后续有关具体配置的方法自己翻各个mod的wiki去.
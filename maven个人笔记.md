**pom文件：Project Object Model项目对象模型**



# 一、Git/Github

## 1. 优点

​			Git 是一个免费的、开源的分布式版本控制系统

​			分布式的版本控制系统出现之后,解决了集中式版本控制系统的缺陷: 1. 服务器断网的情况下也可以进行开发（因为版本控制是在本地进行的） 2. 每个客户端保存的也都是整个完整的项目（包含历史记录，更加安全）

代码托管中心==>远程库

局域网：GitLab

互联网：Github（外网）

​				Gitee 码云 （国内网站）

Git 首次安装必须设置一下用户签名，否则无法提交代码。※注意：这里设置用户签名和将来登录 GitHub（或其他代码托管中心）的账号没有任何关系

## 2.Git 常用命令

git init                  初始化本地库

git add 文件名    将工作区的文件添加到暂存区

git status             查看状态

git commit -m "日志信息" 文件名    将暂存区的文件提交到本地库

cat 文件名            查看文件内容

git reflog              查看版本信息

git log                   查看版本详细信息（Author，Date）

git reset --hard 版本号    版本穿梭（先git reflog 查看各个版本）



Git 切换版本，底层其实是移动的 HEAD 指针

## 

## 3.Git 分支操作

git branch 分支名                创建分支

git branch -v                        查看分支（*代表当前分支）

 git checkout 分支名           切换分支 

git merge 分支名                 把指定的分支合并到当前分支上（被合并的分支不会受影响）

切换分支的本质就是移动 HEAD 指针

产生冲突

```java
冲突产生的表现：后面状态为 MERGING
    
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/SH0720 (master|MERGING)
```

解决冲突：修改冲突内容，添加到暂存区，执行提交（注意：此时使用 git commit 命令时不能带文件名）



## 4.远程仓库操作 

命令名称 														作用 

git remote -v                                                 查看当前所有远程地址别名 

git remote add 别名 远程地址                    起别名 

git push 别名 分支（最小单位）                                        推送本地分支上的内容到远程仓库 

git clone 远程地址                                        将远程仓库的内容克隆到本地 

git pull 远程库地址别名 远程分支名           将远程仓库对于分支最新内容拉下来后与 当前本地分支直接合并

## 5.团队合作

团队内合作：settings-Manage access-invite a collaborator 发送邀请函，然后别人在Github界面地址栏粘贴链接就能加入团队

跨团队合作：先找到branch，再fork---clone---push（到自己的远程仓库）---pull request---审核然后merge pull request合并代码

## 6.idea集成Git

### 6.1配置git忽略文件

​		为什么要忽略他们？     与项目的实际功能无关，不参与服务器上部署运行。把它们忽略掉能够屏蔽 IDE 工具之 间的差异。

​		1）创建忽略规则文件 xxxx.ignore（前缀名随便起，建议是 git.ignore） 这个文件的存放位置原则上在哪里			  都可以，为了便于让~/.gitconfig 文件引用，建议也放在用 户目录下

​		2）在.gitconfig 文件中引用忽略配置文件

```
[user]
name = Layne
email = Layne@atguigu.com
[core]
excludesfile = C:/Users/asus/git.ignore
注意：这里要使用“正斜线（/）”，不要使用“反斜线（\）”
```

​		3）定位Git：idea--settings--version controll--Git 安装目录

​		4）初始化本地库：VCS--create Git Repository

​			  添加到暂存区，右键Git--add

​			  提交到本地库 commit depository

### 6.2 push到远程仓库

​		origin 默认使用https方式，可以自定义ssh方式（将ssh链接复制，点击origin修改）

​		push 是将本地库代码推送到远程库，如果本地库代码跟远程库代码版本不一致， push 的操作是会被拒绝的。也就是说，要想 push 成功，一定要保证本地库的版本要比远程 库的版本高！因此一个成熟的程序员在动手改本地代码之前，一定会先检查下远程库跟本地 代码的区别！如果本地的代码版本已经落后，切记要先 pull 拉取一下远程库的代码，将本地 代码更新到最新以后，然后再修改，提交，推送



# 二、Linux

## 2.1 虚拟机网络连接的三种方式

​			桥接模式：虚拟系统可以和外部进行通讯，但容易造成IP冲突（和母机在一个网段）

​			NAT模式：网络地址转换模式，虚拟系统可以和外部进行通讯，不会造成ip冲突

​			主机模式：独立的系统

## 2.2 VMware Workstation--CentOS

​			虚拟机的克隆、快照、迁移和删除（操作文件夹）

## 2.3 安装vmtools

​			可以设置windows和centos共享文件夹，共享文件夹在centos的/mnt/hgfs 下

vm安装包xxx.tar.gz 拷贝到/opt  使用解压命令 tar 得到安装文件， cd/opt tar -zxvf xxx.tar.gz

安装vmtools 需要有gcc       gcc -v  查看 

## 2.4 Linux的目录结构

##### *在Linux的世界里，一切皆为文件*

## 2.5 远程登录Linux---Xshell7

Xshell可以在Windows界面下用来访问远端不同系统下的服务器，从而达到比较好的远端控制终端的效果

## 2.6 远程上传下载文件---Xftp7

使Windows用户能安全地在UNIX/Linux 和Windows PC之间传输文件，解决乱码--设置UTF-8编码方式

## 2.7 常用命令

**vim                    快捷键**

yy                      拷贝当前行

dd                     删除

/关键字            查找，输入n查找下一个

：set nu       设置行号    :set nonu   

G    gg               到最末行/回到首行

u                      撤销

shift+g              将光标移动多少行



shutdown -h -now            立即关机

shutdown -h 1                  1分钟后关机

reboot                                重启

sync                                    把内存中的数据同步到磁盘

su  -   用户名                          切换用户（-前后都有空格）

logout                                 注销，在图形运行级别无效，在运行级别3下有效

rpm -qa | grep  -i  firefox           查看已安装的rpm列表

rpm -e firefox                               卸载firefox

rpm -ivh RPM包全路径名称         安装rpm包（install 安装， verbose 提示， hash 进度条）

ps  -ef  |  grep  reids                   查看redis进程

systemctl  start mysqld.service        启动mysql

systemctl get-default                 查看默认运行级别（5，graphical.target，cenOS7以前/etc/inittab）



 Linux系统是一个多用户多任务的操作系统，Linux中的用户至少要属于一个组。

shell                                             命令行解释器，我们通过xshell实现远程操作Linux系统就是通过登录                                                                                           

​                                                     shell（bash）来将命令传递给Linux系统实现的

ls -al                                           查看被隐藏文件并列表,Linux下隐藏文件以“.”开头



man指令或help指令      帮助指令

cd 或 cd ~ 回到家目录（/root 或者 /home/tom）

cd /   回到根目录

less      分屏查看文件内容，和more相比，并不是一次将文件加载，对于大文件显示更有效率

cat /etc/profile | less          空格键翻页

“>” 输出重定向  “>>” 追加

tail   -f   文件         实施追踪该文件的更新

ln -s                       软链接（类似快捷方式

history    10（可以不写）              查看10条历史指令，！10  执行第10条历史指令

find /home -user tom     查找指令（-name 、 -user 、 -size  +20M）

grep 过滤查找  ‘ | ’  管道符，表示将前一个命令的输出结果传递给后一个命令处理

tar -zcvf       打包

tar -zxvf  myhome.tar.gz  -C   /opt/temp2         解压    

# 三、Redis

## 1.NoSQL数据库---Not Only SQL

非关系型（缓存）数据库：把数据存储在内存中，减少IO的读操作

配合关系型数据库做高速缓存

## 2.redis安装

redis安装--备份配置文件--修改配置文件 设置后台运行 --访问redis：redis-cli -h 127.0.0.1 -p 6379

关闭客户端：命令行输入exit或快捷键ctrl+c

关闭服务器：shutdown

## 		3.redis特性

###### Redis是单线程+多路IO复用技术（同时监视多个请求的就绪状态【select,pool,epool模式】，如果请求就绪则操作该请求）

多路复用是指使用一个线程来检查多个文件描述符（Socket）的就绪状态，比如调用select和poll函数，传入多个文件描述符，如果有一个文件描述符就绪，则返回，否则阻塞直到超时。得到就绪状态后进行真正的操作可以在同一个线程里执行，也可以启动线程执行（比如使用线程池）

串行  vs  多线程+锁（memcached） vs  单线程+多路IO复用(Redis)  其它区别：2）redis数据类型有5种; 3)redis能持久化数据到本地；	

**原子性**：所谓**原子**操作是指不会被线程调度机制打断的操作；

这种操作一旦开始，就一直运行到结束，中间不会有任何 context switch （切换到另一个线程）。

（1）在单线程中， 能够在单条指令中完成的操作都可以认为是"原子操作"，因为中断只能发生于指令之间。

（2）在多线程中，不能被其它进程（线程）打断的操作就叫原子操作。

Redis单命令的原子性主要得益于Redis的单线程。



## 4.redis(值的)五大数据类型

​										**string**

​                                        **set**：Redis的Set是string类型的无序集合。它底层其实是一个value为null的hash表，所												  以添加，删除，查找的复杂度都是O(1)。

**key              +                  list**

​										**hash**

​										**zset**

### 4.1 Redis 键（key）

keys *查看当前库所有key  (匹配：keys *1)

exists key判断某个key是否存在

type key 查看你的key是什么类型

del key    删除指定的key数据

unlink key  根据value选择非阻塞删除

仅将keys从keyspace元数据中删除，真正的删除会在后续异步操作。

expire key 10  10秒钟：为给定的key设置过期时间

ttl key 查看还有多少秒过期，-1表示永不过期，-2表示已过期

 

select命令切换数据库

dbsize查看当前数据库的key的数量

flushdb清空当前库

flushall通杀全部库

### 4.2 Redis 字符串（String）

​         **String的数据结构为简单动态字符串(Simple Dynamic String,缩写SDS)。是可以修改的字符串，内部结构实现上类似于Java的ArrayList，采用预分配冗余空间的方式来减少内存的频繁分配.**

​	    **内部为当前字符串实际分配的空间capacity一般要高于实际字符串长度len。当字符串长度小于1M时，扩容都是加倍现有的空间，如果超过1M，扩容时一次只会多扩1M的空间。需要注意的是字符串最大长度为512M。**

set  <key><value>添加键值对

get  <key>查询对应键值

append <key><value>将给定的<value> 追加到原值的末尾

strlen <key>获得值的长度

setnx <key><value>只有在 key 不存在时  设置 key 的值

incr <key>        将 key 中储存的数字值增1

​                           只能对数字值操作，如果为空，新增值为1

decr <key>      将 key 中储存的数字值减1

​                          只能对数字值操作，如果为空，新增值为-1

incrby / decrby <key><步长>将 key 中储存的数字值增减。自定义步长

mset <key1><value1><key2><value2> ..... 

同时设置一个或多个 key-value对 

mget <key1><key2><key3> .....

同时获取一个或多个 value 

msetnx <key1><value1><key2><value2> .....

同时设置一个或多个 key-value 对，当且仅当所有给定 key 都不存在。

**原子性，有一个失败则都失败**

 

getrange <key><起始位置><结束位置>

获得值的范围，类似java中的substring，**前包，后包**

setrange <key><起始位置><value>

用 <value> 覆写<key>所储存的字符串值，从<起始位置>开始(**索引从0开始**)。

 

**setex <key><**过期时间**><value>**      设置键值的同时，设置过期时间，单位秒。

getset <key><value>        以新换旧，设置了新值同时获得旧值。

### 4.3 **Redis**列表**(List)**--底层：双向链表

​			**Redis将链表和ziplist（一块连续的内存存储）结合起来组成了quicklist。也就是将多个ziplist使用双向指针串起来使用。这样既满足了快速的插入删除性能，又不会出现太大的空间冗余。**

lpush/rpush <key><value1><value2><value3> .... 从左边/右边插入一个或多个值。

lpop/rpop <key>从左边/右边吐出一个值。值在键在，值光键亡。

 

rpoplpush <key1><key2>从<key1>列表右边吐出一个值，插到<key2>列表左边。

 

lrange <key><start><stop>

按照索引下标获得元素(从左到右)

lrange mylist 0 -1  0左边第一个，-1右边第一个，（0-1表示获取所有）

lindex <key><index>按照索引下标获得元素(从左到右)

llen <key>获得列表长度 

 

linsert <key> before <value><newvalue>在<value>的后面插入<newvalue>插入值

lrem <key><n><value>从左边删除n个value(从左到右)

lset<key><index><value>将列表key下标为index的值替换成value

### **4.4.**  **Redis**集合**(Set)**

​			**Set数据结构是dict字典，字典是用哈希表实现的。Redis的Set是string类型的无序集合。它底层其实是一个value为null的hash表，所以添加，删除，查找的复杂度都是O(1)。**

sadd <key><value1><value2> ..... 

将一个或多个 member 元素加入到集合 key 中，已经存在的 member 元素将被忽略

smembers <key>取出该集合的所有值。

sismember <key><value>判断集合<key>是否为含有该<value>值，有1，没有0

scard<key>返回该集合的元素个数。

srem <key><value1><value2> .... 删除集合中的某个元素。

spop <key>**随机从该集合中吐出一个值。**

srandmember <key><n>随机从该集合中取出n个值。不会从集合中删除 。

smove <source><destination>value把集合中一个值从一个集合移动到另一个集合

sinter <key1><key2>返回两个集合的交集元素。

sunion <key1><key2>返回两个集合的并集元素。

sdiff <key1><key2>返回两个集合的**差集**元素(key1中的，不包含key2中的)

### 4.5 Redis 哈希（hash）

​			**Redis hash是一个string类型的field和value的映射表，hash特别适合用于存储对象。类似Java里面的Map<String,Object>**            

​			**Hash类型对应的数据结构是两种：ziplist（压缩列表），hashtable（哈希表）。当field-value长度较短且个数较少时，使用ziplist，否则使用hashtable。**

hset <key><field><value>给<key>集合中的 <field>键赋值<value>

hget <key1><field>从<key1>集合<field>取出 value 

hmset <key1><field1><value1><field2><value2>... 批量设置hash的值

hexists<key1><field>查看哈希表 key 中，给定域 field 是否存在。 

hkeys <key>列出该hash集合的所有field

hvals <key>列出该hash集合的所有value

hincrby <key><field><increment>为哈希表 key 中的域 field 的值加上增量 1  -1

hsetnx <key><field><value>将哈希表 key 中的域 field 的值设置为 value ，当且仅当域 field 不存在 

### 4.6 Redis 有序集合 zset（sorted set）

​		**SortedSet(zset)是Redis提供的一个非常特别的数据结构，一方面它等价于Java的数据结构Map<String, Double>，可以给每一个元素value赋予一个权重score，另一方面它又类似于TreeSet，内部的元素会按照权重score进行排序，可以得到每个元素的名次，还可以通过score的范围来获取元素的列表。**

**zset底层使用了两个数据结构**

**（1）hash，hash的作用就是关联元素value和权重score，保障元素value的唯一性，可以通过元素value找到相应的score值。**

**（2）跳跃表，跳跃表的目的在于给元素value排序，根据score的范围获取元素列表。跳跃表效率堪比红黑树，实现远比红黑树简单**



# 五、Mysql高级

union  联合查询

数据本身之外，数据库还维护着一个**满足特定查找算法的数据结构**，这些数据结构以某种方式指向数据，这样就可以在这些数据结构的基础上实现高级查找算法，这种数据结构就是索引。

索引:排序好的快速查找数据结构，where 、orderby

数据库delete逻辑上删除



- B树：非叶子节点和叶子节点都会存储数据。

- B+树：只有叶子节点才会存储数据，非叶子节点至存储键值。叶子节点之间使用双向指针连接，最底层的叶子节点形成了一个双向有序链表。

- **B+树可以保证等值和范围查询的快速查找，MySQL的索引就采用了B+树的数据结构。**

  - **MyISAM的数据文件和索引文件是分开存储的。**MyISAM使用B+树构建索引树时，叶子节点中存储的键值为索引列的值，数据为索引所在行的磁盘地址。在 MyISAM 中,辅助索引和主键索引的结构是一样的，没有任何区别，叶子节点的数据存储的都是行记录的磁盘地址。只是主键索引的键值是唯一的，而辅助索引的键值可以重复。查询数据时，由于**辅助索引的键值不唯一，可能存在多个拥有相同的记录，所以即使是等值查询，也需要按照范围查询的方式在辅助索引树中检索数据**

  - **InnoDB的数据和索引存储在一个文件中**。InnoDB的数据组织方式，是聚簇索引。主键索引的叶子节点会存储数据行，辅助索引叶子节点只会存储主键值。底层叶子节点的按照（age，id）的顺序排序，先按照age列从小到大排序，age列相同时按照id列从小到大排序。age 辅助索引  id 主键索引

    **使用辅助索引需要检索两遍索引：首先检索辅助索引获得主键，然后使用主键到主索引中检索获得记录**。根据在辅助索引树中获取的主键id，到主键索引树检索数据的过程称为**回表**查询、

  **组合索引的最左前缀匹配原则：使用组合索引查询时，mysql会一直向右匹配直至遇到范围查询(>、<、between、like)就停止匹配。** 创建的idx_abc(a,b,c)索引，相当于创建了(a)、（a,b）（a,b,c）三个索引。B+树会先比较a列来确定下一步应该搜索的方向，往左还是往右。如果a列相同再比较b列。但是如果查询条件没有a列，B+树就不知道第一步应该从哪个节点查起。

  **覆盖索引（covering index）：**select的数据列只用从索引中就能够获取，不必读取数据行

  **联合索引**，在建立索引的时候，尽量在多个单列索引上判断下是否可以使用联合索引。联合索引的使用不仅可以节省空间，还可以更容易的使用到索引覆盖。试想一下，索引的字段越多，是不是更容易满足查询需要返回的数据呢。比如联合索引（a_b_c），是不是等于有了索引：a，a_b，a_b_c三个索引

  **联合索引的创建原则**，在创建联合索引的时候因该把频繁使用的列、区分度高的列放在前面，频繁使用代表索引利用率高，区分度高代表筛选粒度大，这些都是在索引创建的需要考虑到的优化场景，也可以在常需要作为查询返回的字段上增加到联合索引中，如果在联合索引上增加一个字段而使用到了覆盖索引，那我建议这种情况下使用联合索引。
  ————————————————
  版权声明：本文为CSDN博主「敖 丙」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
  原文链接：https://blog.csdn.net/qq_35190492/article/details/109257302

  
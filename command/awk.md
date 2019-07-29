### 用过的一些awk命令

#### 去除文件第一列

```shell
awk '{$1="";print $0}' file.txt > result.txt
```

或者

```shell
sed -e 's/[^ ]* //' file.txt > result.txt
```

#### 去除文件每一行前后空格

```shell
# cmd.awk
{
    sub(/^[ ]/,"");
    sub(/[ ]$/,"");
    print $0
}
```

```shell
awk -f cmd.awk file.txt > result.txt
```


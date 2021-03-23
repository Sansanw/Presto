# Presto
Learn Presto &amp; Differences between Presto &amp; Hive.

[官方docs](https://prestodb.io/docs/current/)


## 时间
主要区别：
1. hive可以对string - varchar类型的字段做时间变化，相似变化presto只支持Date and Time类型字段。
2. year to month, day to second等作为presto时间函数的变量，而hive多有个函数对应month, year等使用场景。presto更方便。

### 针对区别一：业务表决定。
解决方案：
1. 把varchar转换成timestamp，用presto变化后再转换回varchar。
2. 推荐：**直接用timestamp参与presto变化。**

```
{
  dt >= date_format(now(), '%Y-%m-%d') 
  -- timestamp-> varchar，格式为yyyy-MM-dd，可随自己需要改变
  select  CAST(sysdate( - 1) AS TIMESTAMP)
  -- varchar -> timestamp，格式为yyyy-MM-dd HH:mm:ss
  select  Date(sysdate( - 1))
  -- varchar -> timestamp，格式为yyyy-MM-dd
}
```

扫盲时间：
1. sysdate(0)是string-varchar。
2. now()是TIMESTAMP WITH TIME ZONE，如 *2021-03-23 13:59:19.647 Asia/Shanghai*
> 2021-03-23 13:59:19.647 Asia/Shanghai

### 加减日期
#### Hive
#### Pesto直接做加减
```json
{
now() - interval '1' MONTH
-- YEAR/DAY
}
```


#### Hive

### 返回首天


## 

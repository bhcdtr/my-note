## 错误处理 INSERT 语句与 FOREIGN KEY SAME TABLE 约束冲突
> 问题描述： 插入语句时受约束，报错：
```sql
INSERT 语句与
FOREIGN KEY SAME TABLE 约束"FK__Course__Cpno__276EDEB3"冲突。该冲突发生于数据库"S_T_U201814847"，表"dbo.Course",
column 'Cno'。
语句已终止。
```
> 问题原因： 外键约束（待补充）
> 问题解决： 消除约束即可，如下： ALIER TABLE [表名] DROP CONSTRAINT [约束名]
```sql
ALTER TABLE COURSE
DROP CONSTRAINT FK_Course_Cpno_276EDEB3;
```
### 有时候表名可能不是报错中的表，该问题有待发现更好的解决方案
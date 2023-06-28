## 聚合函数应用
```sql
invClass	invcode	     invname	   cInvStd	      iQuantity
-------------------------------------------------------------------------------
02	         02011	     低碳锰铁	   Mn80C0.4	      2204.360000
02	         02011	     低碳锰铁	   Mn80C0.4	      0.000000
02	         02012	     低碳锰铁	   Mn80C0.7	      0.000000
02	         02014	     高硅硅锰	   60-28	      0.000000
02	         02006	     高硅硅锰	   63-25	      86968.394000
02	         02006	     高硅硅锰	   63-25	      -40600.720000
02	         02014	     高硅硅锰	   60-28	      5310.060000
在这些数据中，将高硅硅锰合并为一行，高硅硅锰的invcode固定为02006,并且保证其他数据不变

要保持其他行的数据不变，只针对特定的 "invname" 进行合并，可以使用子查询或公共表表达式（CTE）来实现
SELECT invClass, invcode, invname, cInvStd, iQuantity
FROM TableNmae
WHERE invname <> '高硅硅锰' -- 排除高硅硅锰的行
UNION ALL --将这些行与下面的聚合结果合并
SELECT invClass, invcode, invname, cInvStd, SUM(iQuantity) AS TotalQuantity
FROM TableName
WHERE invname = '高硅硅锰' -- 选择高硅硅锰的行
GROUP BY invClass, invcode, invname, cInvStd

如果您想让高硅硅锰的"invcode" 固定为 "02006"，可以在查询中直接指定 "invcode" 的值为 "02006"，
即'02006' AS invcode

```
## 删除无关联数据

```sql
    可以使用以下SQL语句来删除B表中与A表无关的数据：

    DELETE FROM B WHERE B.id NOT IN (SELECT id FROM A);
```
# Examples

## Join

```sql
select items.OrderNumber, items.Status, items.ProductID, groups.Status
from [blabla].[order].[TBL_OrderGroups] as groups join [blabla].[order].[TBL_OrderLineItems] as items
on items.OrderNumber = groups.OrderNumber
where groups.LogonName = 'logon_name' and items.Status = 4 and groups.Status != 3
order by OrderNumber desc
```

| WORKER\_ID | FIRST\_NAME | LAST\_NAME | SALARY | JOINING\_DATE | DEPARTMENT |
| ---------- | ----------- | ---------- | ------ | ------------- | ---------- |

Table1 - Worker Table2 – Title\
Write an SQL query to print First name of the Workers who are also Managers

| WORKER\_REF\_ID | WORKER\_TITLE | AFFECTED\_FROM |
| --------------- | ------------- | -------------- |

select work.worker\__id, work.first\__name

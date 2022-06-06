# Examples

## Join

```sql
select groups.Status, items.OrderNumber, items.Status, items.ProductID
from [blabla].[order].[TBL_OrderGroups] as groups 
join [blabla].[order].[TBL_OrderLineItems] as items
on items.OrderNumber = groups.OrderNumber
where groups.LogonName = 'logon_name' and items.Status = 4 and groups.Status != 3
order by OrderNumber desc
```


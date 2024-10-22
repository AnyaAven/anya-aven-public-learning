# Django Queries 

---

## Bitwise NOT operator
`~` is a bitwise NOT operator. 
In this context, it negates the Q object, meaning that the query will return 
all objects not matching the condition inside the Q.
```python
~Q(modelField=ModelField.DELETED)
```
This translates to "give me all records where the giveawayStatus is not equal to GiveawayStatus.DELETED."

## `>` or `<`

`lte` is less than or equal to
`gte` is greater than or equal to

```python
~Q(modelField__lte=ModelField.AMOUNT)
```
or
```python
~Q(modelField__gte=ModelField.AMOUNT)
```
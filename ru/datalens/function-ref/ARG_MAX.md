---
editable: false
---

# ARG_MAX



#### Синтаксис {#syntax}


```
ARG_MAX( value, comp )
```

#### Описание {#description}
Возвращает значение `value`, соответствующее максимальному значению `comp`.

**Типы аргументов:**
- `value` — `Любой`
- `comp` — `Любой`


**Возвращаемый тип**: Совпадает с типом аргументов (`value`)

#### Примеры {#examples}

```
ARG_MAX([Sales], [Profit])
```


#### Поддержка источников данных {#data-source-support}

`Материализованный датасет`, `ClickHouse 1.1`.
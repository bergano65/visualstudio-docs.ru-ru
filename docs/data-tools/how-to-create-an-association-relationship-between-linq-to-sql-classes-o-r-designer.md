---
title: Связи между классами LINQ to SQL (реляционный конструктор R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fb81cf17de86a11d2373f6a545b3efc78e65ada9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586475"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Как создать ассоциацию между классами LINQ to SQL (реляционный конструктор R)
Ассоциации между классами сущностей в [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] аналогичны отношениям между таблицами в базе данных. Ассоциации между классами сущностей можно создавать, используя диалоговое окно **Редактор ассоциаций**.

Можно выбирать родительский класс и дочерний класс, когда диалоговое окно **Редактор ассоциаций** используется для создания ассоциации. Родительский класс представляет собой класс сущностей, который содержит первичный ключ; дочерний класс представляет собой класс сущностей, который содержит внешний ключ. Например, если созданы классы сущностей, сопоставленные с таблицами `Northwind Customers` и `Orders`, то класс `Customer` будет родительским классом, а класс `Order` будет дочерним классом.

> [!NOTE]
> При перетаскивании таблиц из **Обозреватель сервера** или **Обозреватель базы данных** в **Реляционный конструктор объектов** (**Реляционный конструктор O/R**) ассоциации создаются автоматически на основе существующих связей внешнего ключа в базе данных.

## <a name="association-properties"></a>Свойства ассоциации
После создания ассоциации при выборе ассоциации в **реляционном конструкторе объектов** имеются некоторые конфигурируемые свойства в окне **Свойства**. (Ассоциация — это линия между связанными классами.) В следующей таблице приведены описания свойств ассоциации.

|Идентификаторы|Описание|
|--------------|-----------------|
|**Кратность**|Контролирует, представляет ли ассоциация отношение "один-ко-многим" или отношение "один-к-одному".|
|**Дочернее свойство**|Определяет, создавать ли свойство на основе родителя, который является коллекцией, или на основе ссылки на дочерние записи на стороне внешнего ключа ассоциации. Например, в связи между `Customer` и `Order`, если **дочернее свойство** имеет значение **true**, в родительском классе создается свойство с именем `Orders`.|
|**Родительское свойство**|Свойство на основе дочернего класса, который ссылается на связанный родительский класс. Например, в связи между `Customer` и `Order`свойство с именем `Customer`, которое ссылается на связанный клиент для заказа, создается в классе `Order`.|
|**Участвующие свойства**|Отображает свойства ассоциации и выводит кнопку с **многоточием** (...), которая заново открывает диалоговое окно **Редактор ассоциаций**.|
|**Уникальный**|Указывает, имеют ли внешние целевые столбцы ограничение уникальности.|

## <a name="to-create-an-association-between-entity-classes"></a>Для создания ассоциации между классами сущностей

1. Щелкните правой кнопкой мыши по классу сущностей, который представляет родительский класс в ассоциации, укажите пункт **Добавить** и потом щелкните **Ассоциация**.

2. Убедитесь, что выбран правильный **Родительский класс**, в диалоговом окне **Редактор ассоциации**.

3. Выберите **Дочерний класс** в поле со списком.

4. Выберите **Свойства ассоциации**, которые связывают классы. Обычно, это сопоставляется с отношением внешнего ключа, определенным в базе данных. Например, в ассоциации `Customers` и `Orders` **Свойства ассоциации** являются `CustomerID` для каждого класса.

5. Нажмите кнопку **OK** для создания ассоциации.

## <a name="see-also"></a>См. также:

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Пошаговое руководство. Создание классов LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md)
- [Практическое руководство. Представление первичных ключей](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)

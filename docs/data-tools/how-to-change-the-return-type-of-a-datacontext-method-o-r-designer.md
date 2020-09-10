---
title: Изменить тип возвращаемого значения для метода DataContext
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b40851323efdf3c2cbf0900ae323f3c9c0a1ec17
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2020
ms.locfileid: "89737037"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Практическое руководство. Изменение типа значений, возвращаемых методом DataContext (реляционный конструктор объектов)
Тип возвращаемого значения <xref:System.Data.Linq.DataContext> метода (созданного на основе хранимой процедуры или функции) зависит от места удаления хранимой процедуры или функции в **конструкторе O/R**. Если вы сбрасываете элемент прямо в существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возврата создаваемого класса сущностей (если схема данных, возвращенная сохраненной процедурой или функцией совпадает с формой класса сущностей). При перетаскивании элемента в пустую область **конструктора O/R** <xref:System.Data.Linq.DataContext> создается метод, который возвращает автоматически созданный тип. Можно изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext> после его добавления в область методов. Чтобы проверить или изменить тип возврата метода <xref:System.Data.Linq.DataContext>, выберите его и щелкните по свойству **Тип возврата** в окне **Свойства**.

> [!NOTE]
> Нельзя восстановить методы <xref:System.Data.Linq.DataContext> (для которых в качестве типа возвращаемого значения задан класс сущности) таким образом, чтобы они возвращали автоматически созданный тип в окне **Свойства**. Чтобы вернуть <xref:System.Data.Linq.DataContext> метод, возвращающий автоматически созданный тип, необходимо снова перетащить исходный объект базы данных в **конструктор O/R** .

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Чтобы изменить тип возвращаемого значения метода DataContext от автоматически сгенерированного типа к классу сущностей

1. Выберите метод <xref:System.Data.Linq.DataContext> в области методов.

2. Выберите **Тип возвращаемого значения** в окне **Свойства** и потом доступный класс сущностей в списке **Типов возврата**. Если нужный класс сущностей отсутствует в списке, добавьте его в объект или создайте его в **реляционном конструкторе** объектов, чтобы добавить его в список.

3. Сохраните файл *. dbml* .

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Чтобы изменить тип возврата метода DataContext от класса сущностей обратно к автоматически созданному типу.

1. Выберите <xref:System.Data.Linq.DataContext> метод на панели **методы** и удалите его.

2. Перетащите объект базы данных из **Обозреватель сервера** или **Обозреватель базы данных** в пустую область **конструктора O/R**.

3. Сохраните файл *. dbml* .

## <a name="see-also"></a>См. также

- [Инструменты LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Методы DataContext (реляционный конструктор R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Практическое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)

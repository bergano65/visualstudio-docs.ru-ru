---
title: Как выполнить изменение типа возвращаемого значения метода DataContext (реляционный конструктор объектов)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 77d7b98367e343f90827429ad50be91527f7f303
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939441"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Как выполнить изменение типа возвращаемого значения метода DataContext (реляционный конструктор объектов)
Тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод (созданный на основе хранимой процедуры или функции) зависит от того, где вы переместили сохраненную процедуру или функцию в **реляционный конструктор объектов**. Если вы переместили элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возвращаемого значения создаваемого класса сущностей (если схема данных, возвращенная сохраненной процедурой или функцией совпадает с формой класса сущностей). Если Вы сбрасываете элемент на пустую область **реляционный конструктор объектов**, <xref:System.Data.Linq.DataContext> создается метод, который возвращает автоматически сгенерированный тип. Можно изменить тип возврата метода <xref:System.Data.Linq.DataContext> после его добавления в область методов. Чтобы проверить или изменить тип возврата метода <xref:System.Data.Linq.DataContext>, выберите его и щелкните по свойству **Тип возврата** в окне **Свойства**.

> [!NOTE]
>  Нельзя восстановить методы <xref:System.Data.Linq.DataContext> (для которых в качестве типа возвращаемого значения задан класс сущности) таким образом, чтобы они возвращали автоматически созданный тип в окне **Свойства**. Для восстановления метода <xref:System.Data.Linq.DataContext>, чтобы он возвращал автоматически сгенерированный тип, необходимо снова перетащить исходный объект базы данных в **реляционный конструктор объектов**.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Чтобы изменить тип возвращаемого значения метода DataContext от автоматически сгенерированного типа к классу сущностей

1.  Выберите метод <xref:System.Data.Linq.DataContext> в области методов.

2.  Выберите **Тип возвращаемого значения** в окне **Свойства** и потом доступный класс сущностей в списке **Типов возврата**. Если нужного класса сущностей не находится в списке, добавьте или создайте его в **реляционный конструктор объектов** , добавляемый в список.

3.  Сохраните *DBML*-файл.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Чтобы изменить тип возвращаемого значения метода DataContext от класса сущностей обратно к автоматически созданному типу.

1.  Выберите метод <xref:System.Data.Linq.DataContext> в области **методов** и удалите его.

2.  Перетащите объект базы данных из **обозревателя серверов** или **обозреватель баз данных** фигуру на пустую область **реляционный конструктор объектов**.

3.  Сохраните *DBML*-файл.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md)
- [Практическое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
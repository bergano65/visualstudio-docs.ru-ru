---
title: 'Способы: измените тип возвращаемого значения метода DataContext (реляционный конструктор объектов)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5c67d6dea4c64e858acdab25ecc4a6cede6bf262
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089361"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Способы: измените тип возвращаемого значения метода DataContext (реляционный конструктор объектов)
Тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод (созданный на основе хранимой процедуры или функции) зависит от того, где вы переместили сохраненную процедуру или функцию в **реляционный конструктор объектов**. Если вы переместили элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возврата создаваемого класса сущностей (если схема данных, возвращенная сохраненной процедурой или функцией совпадает с формой класса сущностей). Если Вы сбрасываете элемент на пустую область **реляционный конструктор объектов**, <xref:System.Data.Linq.DataContext> создается метод, который возвращает автоматически сгенерированный тип. Можно изменить тип возврата метода <xref:System.Data.Linq.DataContext> после его добавления в область методов. Чтобы проверить или изменить тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод, выберите его и нажмите кнопку **тип возвращаемого значения** свойство в **свойства** окна.

> [!NOTE]
>  Невозможно отменить <xref:System.Data.Linq.DataContext> методы, которые имеют тип возвращаемого значения задан класс сущности, чтобы они возвращали автоматически созданный тип с помощью **свойства** окна. Чтобы отменить <xref:System.Data.Linq.DataContext> метод для возврата автоматически сгенерированного типа необходимо перетащить исходный объект базы данных на **реляционный конструктор объектов** еще раз.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Чтобы изменить тип возвращаемого значения метода DataContext от автоматически сгенерированного типа к классу сущностей

1.  Выберите метод <xref:System.Data.Linq.DataContext> в области методов.

2.  Выберите **тип возвращаемого значения** в **свойства** в класс окна, а затем выберите доступные сущности **тип возвращаемого значения** списка. Если нужного класса сущностей не находится в списке, добавьте или создайте его в **реляционный конструктор объектов** , добавляемый в список.

3.  Сохранить *.dbml* файл.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Чтобы изменить тип возвращаемого значения метода DataContext от класса сущностей обратно к автоматически созданному типу.

1.  Выберите <xref:System.Data.Linq.DataContext> метод в **методы** области и удалите его.

2.  Перетащите объект базы данных из **обозревателя серверов** или **обозреватель баз данных** фигуру на пустую область **реляционный конструктор объектов**.

3.  Сохранить *.dbml* файл.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md)
- [Практическое: создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
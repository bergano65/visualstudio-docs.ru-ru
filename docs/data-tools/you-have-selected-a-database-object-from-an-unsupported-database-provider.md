---
title: Выбран объект базы данных из неподдерживаемого поставщика базы данных
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f3ab7375db8c3adfe769cf1c344937b60695eb25
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Выбран объект базы данных из неподдерживаемого поставщика базы данных

Реляционный конструктор объектов поддерживает только поставщик данных .NET Framework для SQL Server (<xref:System.Data.SqlClient>). Несмотря на то, что можно щелкнуть **ОК** и продолжить работу с объектами из неподдерживаемых поставщиков базы данных, можно испытать неожиданное поведение во время выполнения.

> [!NOTE]
> Поддерживаются только данные о соединениях, которые используют .NET Framework Data Provider for SQL Server.

## <a name="to-correct-this-error"></a>Исправление ошибки

- Нажмите кнопку **ОК**.

   Вы можете продолжить построение классов сущностей, сопоставляемым подключению, которое использует неподдерживаемых поставщиков базы данных. Можно испытать неожиданное поведение, когда используете неподдерживаемых поставщиков базы данных.

    - или -

- Нажмите кнопку **отменить**.

   Действие отменяется. Создайте или используйте данные о подключении, которое использует .NET Framework Provider for SQL Server.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
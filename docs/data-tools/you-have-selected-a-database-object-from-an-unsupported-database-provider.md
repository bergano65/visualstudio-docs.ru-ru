---
title: Выбран объект базы данных из неподдерживаемого поставщика базы данных
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 4efaf92c9f4688d6870c1152be27eb4c8f4ed933
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894445"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Выбран объект базы данных из неподдерживаемого поставщика базы данных

**Реляционный конструктор объектов** поддерживает только поставщик данных .NET Framework для SQL Server (<xref:System.Data.SqlClient>). Хотя можно нажать кнопку **OK** и продолжить работу с объектами из неподдерживаемых поставщиков базы данных, можно испытать неожиданное поведение во время выполнения.

> [!NOTE]
> Поддерживаются только данные о соединениях, которые используют .NET Framework Data Provider for SQL Server.

## <a name="to-correct-this-error"></a>Исправление ошибки

- Нажмите кнопку **ОК**.

   Вы можете продолжить построение классов сущностей, которые сопоставляются соединение, которое использует неподдерживаемый поставщик базы данных. Можно испытать неожиданное поведение, когда используете неподдерживаемых поставщиков базы данных.

    - или -

- Нажмите кнопку **Отмена**.

   Действие отменяется. Создайте или используйте данные о подключении, которое использует .NET Framework Provider for SQL Server.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
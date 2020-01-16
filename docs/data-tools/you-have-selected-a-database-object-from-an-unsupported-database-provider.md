---
title: Выбран объект базы данных из неподдерживаемого поставщика базы данных
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1b7e24604f965a7f518ee7802e2eeb6a84e74ddb
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113274"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Выбран объект базы данных из неподдерживаемого поставщика базы данных

**Конструктор O/R** поддерживает только .NET Framework поставщик данных для SQL Server (<xref:System.Data.SqlClient>). Хотя можно нажать кнопку **OK** и продолжить работу с объектами из неподдерживаемых поставщиков базы данных, можно испытать неожиданное поведение во время выполнения.

> [!NOTE]
> Поддерживаются только данные о соединениях, которые используют .NET Framework Data Provider for SQL Server.

## <a name="options"></a>Options

- Нажмите кнопку **OK**, чтобы продолжить построение классов сущностей, сопоставляемым подключению, которое использует неподдерживаемые поставщики базы данных. Можно испытать неожиданное поведение, когда используете неподдерживаемых поставщиков базы данных.

- Нажмите кнопку **Отмена** , чтобы остановить действие. Создайте или используйте другое подключение к данным, которое использует поставщик .NET Framework для SQL Server.

## <a name="see-also"></a>См. также:

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

---
title: Выбран объект базы данных из неподдерживаемого поставщика базы данных
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 03c2b6b1f22b1d57c98ab8cb90c9c34303c96f96
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919659"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Выбран объект базы данных из неподдерживаемого поставщика базы данных

**Реляционный конструктор объектов** поддерживает только поставщик данных .NET Framework для SQL Server (<xref:System.Data.SqlClient>). Хотя можно нажать кнопку **OK** и продолжить работу с объектами из неподдерживаемых поставщиков базы данных, можно испытать неожиданное поведение во время выполнения.

> [!NOTE]
> Поддерживаются только данные о соединениях, которые используют .NET Framework Data Provider for SQL Server.

## <a name="options"></a>Параметры

- Нажмите кнопку **OK**, чтобы продолжить построение классов сущностей, сопоставляемым подключению, которое использует неподдерживаемые поставщики базы данных. Можно испытать неожиданное поведение, когда используете неподдерживаемых поставщиков базы данных.

- Нажмите кнопку **отменить** остановить действие. Создайте или используйте другое подключение к данным, использующий поставщик данных .NET Framework для SQL Server.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
---
title: Объект от неподдерживаемого поставщика
description: Выбран объект базы данных из неподдерживаемого поставщика базы данных
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 84841c5e0759618430f9c2e4f0146cbc2d21fae9
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036721"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Выбран объект базы данных из неподдерживаемого поставщика базы данных

**Конструктор O/R** поддерживает только поставщик данных .NET Framework для SQL Server ( <xref:System.Data.SqlClient> ). Хотя можно нажать кнопку **OK** и продолжить работу с объектами из неподдерживаемых поставщиков базы данных, можно испытать неожиданное поведение во время выполнения.

> [!NOTE]
> Поддерживаются только данные о соединениях, которые используют .NET Framework Data Provider for SQL Server.

## <a name="options"></a>Параметры

- Нажмите кнопку **OK**, чтобы продолжить построение классов сущностей, сопоставляемым подключению, которое использует неподдерживаемые поставщики базы данных. Можно испытать неожиданное поведение, когда используете неподдерживаемых поставщиков базы данных.

- Нажмите кнопку **Отмена** , чтобы остановить действие. Создайте или используйте другое подключение к данным, которое использует поставщик .NET Framework для SQL Server.

## <a name="see-also"></a>См. также раздел

- [Инструменты LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

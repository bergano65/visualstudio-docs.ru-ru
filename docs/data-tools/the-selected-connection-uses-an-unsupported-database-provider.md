---
title: Выбранное подключение использует неподдерживаемый поставщик базы данных
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e6ebdca67dd87f25111ba48c3d9baa346d00e4db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566141"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Выбранное подключение использует неподдерживаемый поставщик базы данных

Это сообщение появляется при перетаскивании элементов, не использующих поставщик данных .NET Framework для SQL Server из **обозревателя серверов** или **обозреватель баз данных** на [средств LINQ to SQL в визуальном элементе Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**Реляционный конструктор объектов** поддерживает только данные о соединениях, использующих поставщик данных .NET Framework для SQL Server. Допустимы только подключения к Microsoft SQL Server или Microsoft SQL Server Database File.

Чтобы исправить эту ошибку, добавляйте только элементы из подключения к данным, использующих поставщик данных .NET Framework для SQL Server **реляционный конструктор объектов**.

## <a name="see-also"></a>См. также

- <xref:System.Data.SqlClient>
- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

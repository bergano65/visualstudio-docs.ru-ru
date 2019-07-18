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
ms.openlocfilehash: 5fab6be50a9b4c273a7bb911d8afde5cf65d7676
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460583"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Выбранное подключение использует неподдерживаемый поставщик базы данных

Это сообщение появляется при перетаскивании элементов, не использующих поставщик данных .NET Framework для SQL Server из **обозревателя серверов** или **обозреватель баз данных** на [средств LINQ to SQL в визуальном элементе Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**Реляционный конструктор объектов** поддерживает только данные о соединениях, использующих поставщик данных .NET Framework для SQL Server. Допустимы только подключения к Microsoft SQL Server или Microsoft SQL Server Database File.

Чтобы исправить эту ошибку, добавляйте только элементы из подключения к данным, использующих поставщик данных .NET Framework для SQL Server **реляционный конструктор объектов**.

## <a name="see-also"></a>См. также

- <xref:System.Data.SqlClient>
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

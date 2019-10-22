---
title: Выбранное подключение использует неподдерживаемый поставщик базы данных
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ce72f9d4f93db5d4f96bfe54e6cb0d29f4e0727b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639969"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Выбранное подключение использует неподдерживаемый поставщик базы данных

Это сообщение появляется при перетаскивании элементов, не использующих .NET Framework поставщика данных для SQL Server из **Обозреватель сервера** или **обозреватель базы данных** в [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**Реляционный конструктор O/R** поддерживает только подключения к данным, которые используют поставщик .NET Framework для SQL Server. Допустимы только подключения к Microsoft SQL Server или Microsoft SQL Server Database File.

Чтобы исправить эту ошибку, добавьте только элементы из подключений к данным, которые используют .NET Framework поставщик данных для SQL Server в **Реляционный конструктор**объектов.

## <a name="see-also"></a>См. также

- <xref:System.Data.SqlClient>
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

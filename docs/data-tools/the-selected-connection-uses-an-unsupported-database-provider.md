---
title: Неподдерживаемый поставщик базы данных
description: Выбранное подключение использует неподдерживаемый поставщик базы данных
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9ff4120796a40da00e258026d8db84ba6e9dbb21
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743266"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Выбранное подключение использует неподдерживаемый поставщик базы данных

Это сообщение появляется при перетаскивании элементов, не использующих .NET Framework поставщика данных для SQL Server из **Обозреватель сервера** или **обозреватель базы данных** в [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**Реляционный конструктор O/R** поддерживает только подключения к данным, которые используют поставщик .NET Framework для SQL Server. Допустимы только подключения к Microsoft SQL Server или Microsoft SQL Server Database File.

Чтобы исправить эту ошибку, добавьте только элементы из подключений к данным, которые используют .NET Framework поставщик данных для SQL Server в **Реляционный конструктор**объектов.

## <a name="see-also"></a>См. также

- <xref:System.Data.SqlClient>
- [Инструменты LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

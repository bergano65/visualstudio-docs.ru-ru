---
title: Выбранное подключение использует неподдерживаемых поставщиков базы данных | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 199bd6ba18f9ac2e7eecbc13868c8c4bc8e829f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Выбранное подключение использует неподдерживаемый поставщик базы данных
Это сообщение появляется при перетаскивании элементов, не использующих поставщик данных .NET Framework для SQL Server из **обозревателя серверов**/**обозреватель баз данных** на [LINQ to SQL Инструменты Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] поддерживает только данные о соединениях, которые используют .NET Framework Provider для SQL Server. Допустимы только подключения к Microsoft SQL Server или Microsoft SQL Server Database File.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   В [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] из данных о соединениях добавляйте только элементы, которые используют .NET Framework Data Provider for SQL Server.  
  
## <a name="see-also"></a>См. также
<xref:System.Data.SqlClient>  
[Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)  
[Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

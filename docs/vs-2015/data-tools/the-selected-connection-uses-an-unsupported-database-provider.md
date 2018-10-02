---
title: Выбранное подключение использует неподдерживаемый поставщик базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4e38bda495521bf81c6eb4b9a00a0f32620a71fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558966"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Выбранное подключение использует неподдерживаемый поставщик базы данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [выбранное подключение использует неподдерживаемый поставщик базы данных](https://docs.microsoft.com/visualstudio/data-tools/the-selected-connection-uses-an-unsupported-database-provider).  
  
  
Это сообщение появляется при перетаскивании элементов, не использующих поставщик данных .NET Framework для SQL Server из **обозревателя серверов**/**обозреватель баз данных** на [LINQ to SQL Инструменты Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] поддерживает только данные о соединениях, которые используют .NET Framework Provider для SQL Server. Допустимы только подключения к Microsoft SQL Server или Microsoft SQL Server Database File.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   В [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] из данных о соединениях добавляйте только элементы, которые используют .NET Framework Data Provider for SQL Server.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Data.SqlClient>   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Поставщики данных .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Пошаговое руководство: Создание классов LINQ to SQL (реляционный конструктор объектов)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Создание приложений для работы с данными](../data-tools/creating-data-applications.md)


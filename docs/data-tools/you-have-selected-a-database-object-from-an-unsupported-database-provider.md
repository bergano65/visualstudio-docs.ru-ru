---
title: "Выбранный объект базы данных предоставляется неподдерживаемым поставщиком баз данных | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Выбранный объект базы данных предоставляется неподдерживаемым поставщиком баз данных
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) поддерживает только данные о соединениях, которые используют .NET Framework Provider для SQL Server\(<xref:System.Data.SqlClient>\).Хотя можно нажать кнопку **OK** и продолжить работу с объектами из неподдерживаемых поставщиков базы данных, можно испытать неожиданное поведение во время выполнения.  
  
> [!NOTE]
>  Поддерживаются только данные о подключениях, которые используют .NET Framework Data Provider for SQL Server.  
  
### Исправление этой ошибки  
  
-   Нажмите кнопку **OK**, чтобы продолжить построение классов сущностей, сопоставляемым соединению, которое использует неподдерживаемых поставщиков базы данных.Можно испытать неожиданное поведение, когда используете неподдерживаемых поставщиков базы данных.  
  
     либо  
  
-   Нажмите кнопку **Отмена**.  
  
     Действие отменяется.Создайте или используйте данные о подключении, которое использует .NET Framework Provider for SQL Server.  
  
## См. также  
 [Реляционный конструктор объектов](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Поставщики данных .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)
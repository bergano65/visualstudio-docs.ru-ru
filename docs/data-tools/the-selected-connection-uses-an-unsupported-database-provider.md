---
title: "Для выбранного соединения используется неподдерживаемый поставщик баз данных | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Для выбранного соединения используется неподдерживаемый поставщик баз данных
Это сообщение появляется, когда пользователь перетаскивает элементы, которые не используют .NET Framework Data Provider для SQL Server из **Обозревателя серверов**\/**Обозревателя базы данных** на [Реляционный конструктор объектов](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] поддерживает только данные о подключениях, которые используют .NET Framework Provider для SQL Server.Допустимы только соединения с Microsoft SQL Server или Microsoft SQL Server Database File.  
  
### Исправление этой ошибки  
  
-   В [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] из данных о подключениях добавляйте только элементы, которые используют .NET Framework Data Provider for SQL Server.  
  
## См. также  
 <xref:System.Data.SqlClient>   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/ru-ru/360c340d-e5a6-4a7e-a569-e95d500be43d)   
 [Поставщики данных .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Пошаговое руководство. Создание классов LINQ to SQL \(реляционный конструктор объектов\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Создание приложений для работы с данными](../data-tools/creating-data-applications.md)
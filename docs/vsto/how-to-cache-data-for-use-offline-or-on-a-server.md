---
title: "Практическое руководство. Кэширование данных для автономного использования или для использования на сервере | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "данные [разработка решений Office в Visual Studio], кэширование"
  - "кэширование данных [разработка решений Office в Visual Studio], автономное использование"
  - "кэширование данных [разработка решений Office в Visual Studio], использование сервера"
  - "наборы данных [разработка решений Office в Visual Studio], кэширование"
  - "Office - приложения [разработка решений Office в Visual Studio], данные"
  - "автономные данные [разработка решений Office в Visual Studio]"
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Практическое руководство. Кэширование данных для автономного использования или для использования на сервере
  Можно пометить элемент данных, который следует кэшировать в документе, чтобы он был доступен автономно.  Также можно сделать возможным программное управление данными в документе, хранящемся на сервере.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Можно пометить элемент данных, который следует кэшировать, если элемент данных объявлен в вашем коде, или, если Вы используете <xref:System.Data.DataSet>, с помощью свойства в окне **Свойства**.  Если кэшируется элемент данных, не являющийся <xref:System.Data.DataSet> или <xref:System.Data.DataTable>, убедитесь в том, что он соответствует критериям кэширования в документе.  Дополнительные сведения см. в разделе [Кэширование данных](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Наборы данных, созданные при помощи Visual Basic и помеченные как **Cached** и **WithEvents** \(включая наборы данных, взятых из окна **Источники данных** или из окна **Панель элементов**, свойство **CacheInDocument** которого установлено равным **True**\), содержат подчеркивания в своих именах в кэше.  Например, если создается набор данных с именем Customers, имя <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> в кэше будет \_Customers.  При использовании <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> для доступа к этому кэшированному элементу, необходимо указывать \_Customers, а не Customers.  
  
### Кэширование данных в документе при помощи кода  
  
1.  Объявите открытое поле или свойство для элемента данных как член ведущего класса элементов в проекте, например, класс `ThisDocument` в проекте Word или класс `ThisWorkbook` в проекте Excel.  
  
2.  Примените атрибут <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> к члену для отметки элемента данных, подлежащего сохранению в кэше данных документа.  Следующий пример применяет этот атрибут к объявлению поля для <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#11)]  
  
3.  Добавьте код для создания экземпляра элемента данных и, если применимо, загрузки его из базы данных.  
  
     Элемент данных загружается, если только он был создан в первый раз; после этого в кэше остается документ, и следует написать другой код, чтобы обновить его.  
  
### Кэширование набора данных в документе при помощи окна "Свойства"  
  
1.  Добавьте набор данных в проект при помощи инструментов конструктора Visual Studio, например, используя окно **Источники данных**.  
  
2.  Создайте экземпляр набора данных, если он еще не создан, и выберите экземпляр в конструкторе.  
  
3.  В окне **Свойства** установите свойству **CacheInDocument** значение **True**.  
  
     Дополнительные сведения см. в разделе [Свойства в проектах Office](../vsto/properties-in-office-projects.md).  
  
4.  В окне **Свойства** установите, что свойство **Модификаторы** равным **Общедоступный** \(по умолчанию оно равно **Для внутреннего использования**\).  
  
## См. также  
 [Кэширование данных](../vsto/caching-data.md)   
 [Практическое руководство. Программное кэширование источника данных в документе MS Office.](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Практическое руководство. Кэширование данных в документе, защищенном паролем](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Сохранение данных](../data-tools/saving-data.md)  
  
  
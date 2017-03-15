---
title: "Практическое руководство. Сохранение набора данных в формате XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "данные [Visual Studio], сохранение как XML"
  - "наборы данных [Visual Basic], сохранение как XML"
  - "сохранение данных"
  - "XML [Visual Basic], наборы данных"
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Практическое руководство. Сохранение набора данных в формате XML
К данным XML в наборе данных можно получить доступ, вызывая методы XML, доступные в наборе.  Для сохранения данных в формате XML можно вызвать либо метод <xref:System.Data.DataSet.GetXml%2A>, либо метод <xref:System.Data.DataSet.WriteXml%2A> <xref:System.Data.DataSet>.  
  
 Метод <xref:System.Data.DataSet.GetXml%2A> возвращает строку, содержащую данные из всех таблиц в наборе данных в формате XML\-данных.  
  
 Метод <xref:System.Data.DataSet.WriteXml%2A> отправляет данные в формате XML в указанный файл.  
  
### Чтобы сохранить данные из набора данных в формате XML в переменную  
  
-   Метод <xref:System.Data.DataSet.GetXml%2A> возвращает <xref:System.String>, поэтому объявите переменную типа <xref:System.String> и присвойте ей результаты метода <xref:System.Data.DataSet.GetXml%2A>.  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-cs[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### Чтобы сохранить данные из набора данных в формате XML в файле  
  
-   Метод <xref:System.Data.DataSet.WriteXml%2A> имеет несколько перегрузок.  Следующий фрагмент кода иллюстрирует сохранение данных в файле, поэтому объявите переменную и присвойте ей правильный путь для сохранения файла.  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-cs[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## См. также  
 [Объекты DataSet, DataTable и DataView](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)   
 [Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)   
 [Подготовка приложения к получению данных](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения к получению данных](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](../Topic/Validating%20Data.md)   
 [Сохранение данных](../data-tools/saving-data.md)
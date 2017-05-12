---
title: "Практическое руководство. Программное кэширование источника данных в документе MS Office."
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
  - "кэширование данных [разработка решений Office в Visual Studio], программно"
  - "наборы данных [разработка решений Office в Visual Studio], кэширование"
  - "Office - приложения [разработка решений Office в Visual Studio], данные"
  - "StartCaching - метод"
ms.assetid: 70b3fc06-7534-407e-898b-36f84e9a7516
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Практическое руководство. Программное кэширование источника данных в документе MS Office.
  В документе объект данных добавляется к кэшированным данным с помощью программных средств и метода ведущего элемента `StartCaching`, такого как <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook> или <xref:Microsoft.Office.Tools.Excel.Worksheet>.  Удаляет объект данных из кэша данных посредством вызова метода `StopCaching` ведущего элемента управления.  
  
 Метод `StartCaching` и метод `StopCaching` являются частными, одна оба присутствуют в IntelliSense.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Во время использования метода `StartCaching` добавления объекта данных к кэшированным данным объект данных не обозначается атрибутом <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  Однако объект данных обязан выполнять определенные требования для последующего присоединения к кэшированным данным.  Дополнительные сведения см. в разделе [Кэширование данных](../vsto/caching-data.md).  
  
### Добавление объекта данных в кэш программным образом  
  
1.  Обозначьте объект данных не в методе, а на уровне класса.  На данном примере показывается обозначение <xref:System.Data.DataSet> с названием `dataSet1` и добавление данных в кэш\-память программным способом.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#12)]  
  
2.  Обработайте объект данных, потом запустите метод `StartCaching` в документе или экземпляре листа и укажите в названии объекта данных.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#13)]  
  
### Прекращение кэширования объекта данных  
  
1.  Вызовите метод `StopCaching` экземпляра документа или листа и передайте имя объекта данных.  В этом примере предполагается, что уже существует объект данных <xref:System.Data.DataSet> с именем `dataSet1`, кэширование которого нужно остановить.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  Не вызывайте `StopCaching` из обработчика событий для события `Shutdown` документа или листа.  К тому времени, когда произошло событие `Shutdown`, уже слишком поздно изменять кэш данных.  Дополнительные сведения о событии `Shutdown` см. в разделе [События в проектах Office](../vsto/events-in-office-projects.md).  
  
## См. также  
 [Кэширование данных](../vsto/caching-data.md)   
 [Практическое руководство. Кэширование данных для автономного использования или для использования на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Практическое руководство. Кэширование данных в документе, защищенном паролем](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Сохранение данных](../data-tools/saving-data.md)  
  
  
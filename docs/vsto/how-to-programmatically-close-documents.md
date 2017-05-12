---
title: "Практическое руководство. Программное закрытие документов"
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
  - "документы [разработка решений Office в Visual Studio], закрытие"
  - "Word [разработка решений Office в Visual Studio], закрытие документов"
ms.assetid: d5bee1dc-63d1-4307-828f-b7b077e20fb9
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Практическое руководство. Программное закрытие документов
  Можно закрыть активный документ или указать документ для закрытия.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Закрытие активного документа  
 Для закрытия активного документа можно использовать две процедуры: одну для настроек на уровне документа и одну для надстроек VSTO.  
  
#### Закрытие активного документа в настройке на уровне документа  
  
1.  Для закрытия документа, связанного с настройкой, вызовите метод <xref:Microsoft.Office.Tools.Word.Document.Close%2A> класса `ThisDocument` в своем проекте. Чтобы использовать следующий пример кода, запустите его из класса `ThisDocument`.  
  
    > [!NOTE]  
    >  В этом примере значение <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> передается в параметр *SaveChanges*, чтобы закрыть окно без сохранения изменений или без вывода запросов пользователю.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomation#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#3)]  
  
#### Закрытие активного документа в надстройке VSTO  
  
1.  Для закрытия активного документа вызовите метод <xref:Microsoft.Office.Interop.Word._Document.Close%2A> свойства <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A>. Чтобы использовать следующий пример кода, выполните его из класса `ThisAddIn` в своем проекте.  
  
    > [!NOTE]  
    >  В этом примере значение <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> передается в параметр *SaveChanges*, чтобы закрыть окно без сохранения изменений или без вывода запросов пользователю.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Закрытие документа с заданным именем  
 Процедура закрытия документа с заданным именем идентична процедуре для надстройки VSTO и настроек на уровне документа.  
  
#### Закрытие документа с заданным именем  
  
1.  Укажите имя документа в качестве аргумента для коллекции <xref:Microsoft.Office.Interop.Word._Application.Documents%2A>, а затем вызовите метод <xref:Microsoft.Office.Interop.Word._Document.Close%2A>. В приведенном ниже примере кода предполагается, что в Word открыт документ с именем **NewDocument**.  
  
    > [!NOTE]  
    >  В этом примере значение <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> передается в параметр *SaveChanges*, чтобы закрыть окно без сохранения изменений или без вывода запросов пользователю.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreWordAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#4)]  
  
## См. также  
 [Практическое руководство. Программное открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Практическое руководство. Программное сохранение документов](../vsto/how-to-programmatically-save-documents.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  
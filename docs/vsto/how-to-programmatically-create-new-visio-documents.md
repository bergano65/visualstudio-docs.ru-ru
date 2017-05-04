---
title: "Практическое руководство. Программное создание документов Visio | Microsoft Docs"
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
  - "Visio [разработка решений Office в Visual Studio], создание документов Visio"
  - "документы [разработка решений Office в Visual Studio], создание документов Visio"
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Практическое руководство. Программное создание документов Visio
  При создании нового документа Microsoft Office Visio вы добавляете его в коллекцию Microsoft.Office.Interop.Visio.Documents открытых документов Visio. Соответственно, метод Microsoft.Office.Interop.Visio.Documents.Add создает новый документ Visio. Дополнительные сведения см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241).  
  
## Создание новых пустых документов  
  
#### Создание нового документа  
  
-   Используйте метод Microsoft.Office.Interop.Visio.Documents.Add для создания нового пустого документа не на основе шаблона.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#1)]  
  
## Создание документов, скопированных из существующих документов  
 Метод Microsoft.Office.Interop.Visio.Documents.Add может создать новый документ, который является копией существующего документа Visio. Вы должны указать имя файла и полный путь к диаграмме.  
  
#### Создание нового документа, скопированного из существующего документа  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Documents.Add и укажите путь к диаграмме Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#2)]  
  
## Создание наборов элементов, скопированных из существующих наборов элементов  
 Метод [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241) может создать новый набор элементов, который является копией существующего набора элементов Visio. Вы должны указать имя файла и полный путь к набору элементов.  
  
#### Создание нового набора элементов, скопированного из существующего набора элементов  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Documents.Add и укажите путь к набору элементов.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Создание документов на основе существующих шаблонов  
 Метод Microsoft.Office.Interop.Visio.Documents.Add может создать новый документ \(VSD\-файл\), основанный на существующем шаблоне Visio \(VST\-файле\). Этот метод копирует наборы элементов, стили и параметры, которые являются частью рабочей области шаблона. Необходимо указать имя файла и полный путь к шаблону.  
  
#### Создание нового документа на основе существующего шаблона  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Documents.Add и укажите путь к шаблону.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Документ Visio с именем `myDrawing.vsd` должен быть расположен в каталоге с именем `Test` в папке "Мои документы" \(для Windows XP и более ранних версий\) или в папке "Документы" \(для Windows Vista\).  
  
-   Документ Visio с именем `myStencil.vss` должен быть расположен в каталоге с именем `Test` в папке "Мои документы" \(для Windows XP и более ранних версий\) или в папке "Документы" \(для Windows Vista\).  
  
-   Документ Visio с именем `myTemplate.vst` должен быть расположен в каталоге с именем `Test` в папке "Мои документы" \(для Windows XP и более ранних версий\) или в папке "Документы" \(для Windows Vista\).  
  
## См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)   
 [Практическое руководство. Программное открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Практическое руководство. Программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Практическое руководство. Программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Практическое руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  
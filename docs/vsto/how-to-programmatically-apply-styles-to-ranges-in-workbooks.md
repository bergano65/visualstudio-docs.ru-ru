---
title: "Практическое руководство. Программное применение стилей к диапазонам в книгах | Microsoft Docs"
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
  - "диапазоны, стили"
  - "стили, диапазоны книги"
  - "книги, стили"
ms.assetid: c7e781ed-f366-45bb-aeb6-69c10d19d842
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Практическое руководство. Программное применение стилей к диапазонам в книгах
  К областям в книгах можно применять именованные стили. В Excel реализовано несколько предварительно определенных стилей.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В диалоговом окне **Формат ячеек** отображаются все параметры, которые можно использовать для форматирования ячеек, причем каждый такой параметр доступен из кода. Для отображения этого диалогового окна в Excel щелкните пункт **Ячейки** в меню **Формат**.  
  
### Применение стиля к именованному диапазону в настройке на уровне документа  
  
1.  Создайте новый стиль и задайте его атрибуты.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#53)]  
  
2.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange>, назначьте ему текст, а затем примените новый стиль. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#54](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#54)]  
  
### Удаление стиля из именованного диапазона в настройке на уровне документа  
  
1.  Примените к диапазону стиль «Обычный». Этот код следует разместить в классе листа, а не в классе `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#55](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#55)]  
  
### Применение стиля к именованному диапазону в надстройке VSTO  
  
1.  Создайте новый стиль и задайте его атрибуты.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#28)]  
  
2.  Создайте <xref:Microsoft.Office.Interop.Excel.Range>, назначьте ему текст, а затем примените новый стиль.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#29)]  
  
### Удаление стиля из именованного диапазона в надстройке VSTO  
  
1.  Примените к диапазону стиль «Обычный».  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#56](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#56)]  
  
## См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  
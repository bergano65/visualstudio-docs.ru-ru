---
title: "Практическое руководство. Программное отображение строки в ячейке листа"
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
  - "текст [разработка решений Office в Visual Studio], добавление к листам"
  - "листы, отображение текста в ячейках"
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Практическое руководство. Программное отображение строки в ячейке листа
  В данном примере рассматривается программный способ отображения текста в ячейке.  Для отображения текста в ячейке используйте либо элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange>, либо собственный объект Excel "диапазон".  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Использование элемента управления NamedRange  
 В данном примере используется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `message`.  Элемент управления необходимо добавить в настройку уровня документа на этапе разработки.  Данный код необходимо поместить в класс листа, а не в класс `ThisWorkbook`.  
  
#### Отображение текста в элементе управления NamedRange  
  
1.  Установите для элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> значение **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#68)]  
  
## Использование собственного диапазона Excel  
 В следующем примере кода показано программное создание нового диапазона и присвоение ему значения.  
  
#### Отображение текста в диапазоне Excel  
  
1.  Извлеките диапазон в ячейку **A1** листа `Sheet1` и установите для него значение **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#69)]  
  
## См. также  
 [Пошаговое руководство. Сбор данных с использованием формы Windows Forms](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Устранение неполадок при работе с решениями Office](../vsto/troubleshooting-office-solutions.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  
---
title: "Практическое руководство. Программное расширение диапазонов в документах"
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
  - "диапазоны, расширение"
  - "документы [разработка решений Office в Visual Studio], расширение диапазонов"
ms.assetid: 055af7a4-13d5-4236-b5fb-a112721482c5
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Практическое руководство. Программное расширение диапазонов в документах
  После определения объекта <xref:Microsoft.Office.Interop.Word.Range> в документе Microsoft Office Word вы изменяете его начальную и конечную точки с помощью методов <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> и <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A>. Методы <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> и <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> принимают те же два аргумента, *Unit* и *Count*. Аргумент *Count* — это количество единиц для перемещения, и аргумент *Unit* может иметь одно из следующих <xref:Microsoft.Office.Interop.Word.WdUnits> значений:  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 В следующем примере определяется диапазон в семь символов. Затем начальная позиция этого диапазона перемещается на семь символов после исходной начальной позиции. Поскольку конечная позиция диапазона также находится через семь символов после начальной позиции, результатом является диапазон, состоящий из нуля символов. Затем код перемещает конечную позицию на семь символов после текущей конечной позиции.  
  
### Расширение диапазона  
  
1.  Определите диапазон символов. Для получения дополнительной информации см. [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
     Следующий пример кода можно использовать в настройке на уровне документа.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#39)]
     [!code-vb[Trin_VstcoreWordAutomation#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#39)]  
  
     Приведенный ниже пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#39)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#39)]  
  
2.  Используйте метод <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> объекта <xref:Microsoft.Office.Interop.Word.Range>, чтобы переместить начальную позицию диапазона.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#40](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#40)]
     [!code-vb[Trin_VstcoreWordAutomation#40](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#40)]  
  
3.  Используйте метод <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> объекта <xref:Microsoft.Office.Interop.Word.Range>, чтобы переместить конечную позицию диапазона.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#41](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#41)]
     [!code-vb[Trin_VstcoreWordAutomation#41](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#41)]  
  
## Код настройки на уровне документа  
  
#### Расширение диапазона в настройке на уровне документа  
  
1.  В следующем примере показан полный код для настройки на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#38)]
     [!code-vb[Trin_VstcoreWordAutomation#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#38)]  
  
## Код надстройки VSTO  
  
#### Расширение диапазона в надстройке VSTO уровня приложения  
  
1.  В следующем примере показан полный код для надстройки VSTO. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#38)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#38)]  
  
## См. также  
 [Практическое руководство. Программный сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Практическое руководство. Программное свертывание диапазонов и выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Практическое руководство. Программное извлечение символов начала и завершения в диапазонах](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Практическое руководство. Программное исключение знаков абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  
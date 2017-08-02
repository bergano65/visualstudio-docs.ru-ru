---
title: "Практическое руководство. Программный поиск текста в диапазонах ячеек на листе"
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
  - "текст [разработка решений Office в Visual Studio], поиск в листах"
  - "текстовый поиск, листы"
  - "листы, поиск"
ms.assetid: a6902711-fefb-450a-a76b-b1446d11c423
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Практическое руководство. Программный поиск текста в диапазонах ячеек на листе
  Метод <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> объекта <xref:Microsoft.Office.Interop.Excel.Range> позволяет выполнить поиск текста внутри диапазона.  Этот текст также может быть любой строкой ошибки, которая может появляться в ячейке листа, например `#NULL!` или `#VALUE!`.  Дополнительные сведения о строках ошибок см. в разделе [Значения ошибок для ячеек](HV10038459).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Приведенный ниже пример выполняет поиск в диапазоне с именем `Fruits` и изменяет параметры шрифта ячеек, которые содержат слово "apples".  В этой процедуре также вызывается метод <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>, который использует предыдущий набор настроек повторения поиска.  Указывается ячейка, после которой начинать поиск, и метод <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> анализирует оставшуюся часть диапазона.  
  
> [!NOTE]  
>  После достижения конца диапазон метод <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> продолжает поиск с его начала.  Код должен не допустить вход в бесконечный цикл.  В этом примере показан один из способов решения этой задачи — с помощью свойства <xref:Microsoft.Office.Interop.Excel.Range.Address%2A>.  
  
 ![ссылка на видео](~/data-tools/media/playvideo.gif "ссылка на видео") Для просмотра связанных демонстрационных видеороликов перейдите по ссылке [How Do I: Use the Find Method in an Excel Add\-in?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
### Выполнение поиска текста в диапазоне ячеек на листе  
  
1.  Объявить переменные для хранения первого найденного диапазона и текущего найденного диапазона.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#58)]  
  
2.  Выполнить первый поиск, указав все параметры, кроме ячейки, после которой следует искать.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#59)]  
  
3.  Продолжать поиск, пока есть совпадения.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#60)]  
  
4.  Сравнить первый найденный диапазон \(`firstFind`\) с **Nothing**.  Если переменная `firstFind` не содержит значения, сохранить в ней найденный диапазон \(`currentFind`\).  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#61)]  
  
5.  Выйти из цикла, если адрес найденного диапазона совпадает с адресом первого найденного диапазона.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#62)]  
  
6.  Изменить внешний вид найденного диапазона.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#63)]  
  
7.  Выполнить следующий поиск.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#64)]  
  
 Ниже приведен полный пример метода.  
  
## Пример  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#57)]  
  
## См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Практическое руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Практическое руководство. Ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  
---
title: Как выполнить Программный поиск текста в диапазонах листа
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 37f59f2888fc5a572029f4c21116281df008706e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868593"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Как выполнить Программный поиск текста в диапазонах листа
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> Метод <xref:Microsoft.Office.Interop.Excel.Range> позволяет искать текст в диапазоне. Этот текст может также быть любой из строки ошибок, которые могут отображаться в ячейке листа, такие как `#NULL!` или `#VALUE!`. Дополнительные сведения о строках ошибок см. в разделе [ошибка значений ячеек](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Следующий пример выполняет поиск в диапазоне с именем `Fruits` и изменяет параметры шрифта для ячеек, содержащих слово «apples». В этой процедуре также используется <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> метод, который использует предыдущий набор параметров, чтобы повторить поиск поиска. Указывается ячейка, после которого следует выполнить поиск и <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> всем остальным занимается метод.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Метода поиск с начала диапазона поиска после достижения конца диапазона. Код необходимо убедиться, что поиск не обтекает бесконечный цикл. В этом примере показан один из способов обработки это с помощью <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> свойство.  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") демонстрационные видеоматериалы см. в разделе [инструкции: Использование методов Find в надстройке Excel? ](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
## <a name="to-search-for-text-in-a-worksheet-range"></a>Для поиска текста в диапазоне листа  
  
1. Объявление переменных для отслеживания весь диапазон первого найденного диапазона и текущего найденного диапазона.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2. Найдите первое совпадение, указав все параметры, за исключением ячейки для поиска.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3. Продолжайте поиск до тех пор, пока совпадения.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4. Сравнение первого найденного диапазона (`firstFind`) для **ничего не**. Если `firstFind` не содержит значения, сохранить найденного диапазона (`currentFind`).  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5. Выйти из цикла, если адрес найденного диапазона совпадает с адресом первого найденного диапазона.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6. Задайте внешний вид найденного диапазона.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7. Выполните новый поиск.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
   В следующем примере показан полный метод.  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Практическое руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Практическое руководство. Ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  

---
title: 'Как: программный поиск текста в диапазонах листа | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2749834f459085b8d182b58f12a4c372f7493cba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Практическое руководство. Программный поиск текста в диапазонах ячеек на листе
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> Метод <xref:Microsoft.Office.Interop.Excel.Range> позволяет искать текст в диапазоне. Этот текст также может иметь строки ошибок, которые могут присутствовать в ячейку листа, таких как `#NULL!` или `#VALUE!`. Дополнительные сведения о строках ошибок см. в разделе [значения ячеек ошибки](http://msdn.microsoft.com/library/office/ff839168.aspx).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Следующий пример просматривает диапазон с именем `Fruits` и изменяет параметры шрифта для ячеек, содержащих слово «apples». Эта процедура также используется <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> метод, который использует предыдущий набор настроек повторения поиска. Укажите ячейку, после которого необходимо выполнить поиск и <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> метод обрабатывает rest.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Метода поиск с начала диапазона поиска после достижения конца диапазона. Код необходимо убедиться, что поиск вход в бесконечный цикл. В этом примере показано, как обрабатывать это с помощью <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> свойство.  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [практические советы. Использование метода поиска в надстройке Excel?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
### <a name="to-search-for-text-in-a-worksheet-range"></a>Для поиска текста в диапазоне листа  
  
1.  Объявление переменных для отслеживания весь диапазон, первого найденного диапазона и текущего найденного диапазона.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2.  Найдите первое совпадение, указав все параметры, кроме ячейки для поиска.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3.  Продолжайте поиск при условии, что совпадений.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4.  Сравнение первого найденного диапазона (`firstFind`) для **ничего не**. Если `firstFind` не содержит значения, сохранить найденного диапазона (`currentFind`).  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5.  Выйти из цикла, если адрес найденного диапазона совпадает с адресом первого найденного диапазона.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6.  Задайте внешний вид найденного диапазона.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7.  Выполните поиск.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
 В следующем примере показан полный метод.  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Как: программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Как: ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  
---
title: Практическое руководство. Создание новых книг программным способом
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 030bc801399ddcc73f145c0b45ca065c9a9ecc7a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251878"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Практическое руководство. Создание новых книг программным способом
  При создании книги программными средствами она является собственным объектом <xref:Microsoft.Office.Interop.Excel.Workbook>, а не ведущим элементом <xref:Microsoft.Office.Tools.Excel.Workbook>.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 В проекте надстройки VSTO можно создать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Workbook> для объекта <xref:Microsoft.Office.Interop.Excel.Workbook>. Дополнительные сведения см. [в разделе Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-workbook"></a>Создание новой книги

1. Используйте метод <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Workbooks> .

     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]

    > [!NOTE]
    > Книгу можно создать на основе шаблона, отличного от шаблона по умолчанию: для этого требуемый шаблон следует передать в качестве параметра в метод <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>.

## <a name="see-also"></a>См. также
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Практическое руководство. Открытие книг программными средствами](../vsto/how-to-programmatically-open-workbooks.md)
- [Практическое руководство. Сохранение книг программными средствами](../vsto/how-to-programmatically-save-workbooks.md)
- [Практическое руководство. Программное закрытие книг](../vsto/how-to-programmatically-close-workbooks.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)

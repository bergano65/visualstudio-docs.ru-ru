---
title: Проверять данные при добавлении новой строки в элемент управления ListObject
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f65bbc374c1d0ec2a940ff98fcc6f04e5391b2db
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255682"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Практическое руководство. Проверять данные при добавлении новой строки в элемент управления ListObject
  Пользователи могут добавлять новые строки в элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным. Вы можете проверять данные пользователя перед фиксацией изменений в источнике данных.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Проверка данных
 Каждый раз, когда строка добавляется в <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным, возникает событие <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> . Это событие можно обработать для выполнения проверки данных. Например, если приложению требуется, чтобы в источник данных можно было добавлять только сотрудников из 18 лет и 65, убедитесь, что введенный возраст находится в пределах диапазона перед добавлением строки.

> [!NOTE]
> Всегда следует проверять входные данные пользователя на сервере, как и на клиенте. Дополнительные сведения см. в разделе [безопасные клиентские приложения](/dotnet/framework/data/adonet/secure-client-applications).

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Проверка данных при добавлении новой строки в элемент управления ListObject с привязкой к данным

1. Создайте переменные для идентификатора и объекта <xref:System.Data.DataTable> на уровне класса.

     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]

2. Создайте новый <xref:System.Data.DataTable> объект и добавьте в него `Startup` образцы столбцов и данных в обработчике `Sheet1` событий класса (в проекте уровня документа) или `ThisAddIn` в классе (в проекте надстройки VSTO).

     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]

3. Добавьте код в обработчик событий `list1_BeforeAddDataBoundRow` , чтобы проверить, попадает ли возраст в допустимый диапазон.

     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]

## <a name="compile-the-code"></a>Компиляция кода
 В этом примере кода предполагается, что в листе, в котором этот код появляется, имеется существующий элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с именем `list1` .

## <a name="see-also"></a>См. также
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Элемент управления ListObject](../vsto/listobject-control.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Практическое руководство. Сопоставьте столбцы ListObject с данными](../vsto/how-to-map-listobject-columns-to-data.md)

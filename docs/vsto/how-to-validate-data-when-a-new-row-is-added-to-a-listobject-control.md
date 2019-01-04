---
title: Как выполнить Проверка данных при добавлении новой строки в элемент управления ListObject
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1f6fd03238f9b477f7530353b8b10afb71a41edd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989845"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Как выполнить Проверка данных при добавлении новой строки в элемент управления ListObject
  Пользователи могут добавлять новые строки в элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным. Вы можете проверять данные пользователя перед фиксацией изменений в источнике данных.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="data-validation"></a>Проверка данных  
 Каждый раз, когда строка добавляется в <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным, возникает событие <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> . Это событие можно обработать для выполнения проверки данных. Например если приложение требует, что только сотрудников в возрасте от 18 до 65 могут добавляться к источнику данных, убедитесь, что возраст попадает в пределах диапазона, перед добавлением строки.  
  
> [!NOTE]  
>  Всегда следует проверять входные данные пользователя на сервере, как и на клиенте. Дополнительные сведения см. в разделе [безопасные клиентские приложения](/dotnet/framework/data/adonet/secure-client-applications).  
  
### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Проверка данных при добавлении новой строки в элемент управления ListObject с привязкой к данным  
  
1.  Создайте переменные для идентификатора и объекта <xref:System.Data.DataTable> на уровне класса.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]  
  
2.  Создайте новый <xref:System.Data.DataTable> и добавьте примеры столбцов и данных в `Startup` обработчик событий `Sheet1` класса (в проекте уровня документа) или `ThisAddIn` класса (в проекте надстройки VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]  
  
3.  Добавьте код в обработчик событий `list1_BeforeAddDataBoundRow` , чтобы проверить, попадает ли возраст в допустимый диапазон.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 В этом примере кода предполагается, что в листе, в котором этот код появляется, имеется существующий элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с именем `list1` .  
  
## <a name="see-also"></a>См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Элемент управления ListObject](../vsto/listobject-control.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Практическое руководство. Сопоставления столбцов ListObject с данными](../vsto/how-to-map-listobject-columns-to-data.md)  

---
title: 'Как: проверка данных при добавлении новой строки в элемент управления ListObject'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 55dc8852952482914bc57a41579163c90672d1db
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268364"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Как: проверка данных при добавлении новой строки в элемент управления ListObject
  Пользователи могут добавлять новые строки в элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным. Вы можете проверять данные пользователя перед фиксацией изменений в источнике данных.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="data-validation"></a>Проверка данных  
 Каждый раз, когда строка добавляется в <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным, возникает событие <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> . Это событие можно обработать для выполнения проверки данных. Например если приложение требует, что только сотрудники в возрасте от 18 до 65 могут добавляться к источнику данных, проверьте, попадает ли возраст в пределах диапазона перед добавлением строки.  
  
> [!NOTE]  
>  Всегда следует проверять входные данные пользователя на сервере, как и на клиенте. Дополнительные сведения см. в разделе [защищенные клиентские приложения](/dotnet/framework/data/adonet/secure-client-applications).  
  
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
 [Как: столбцов элемента управления ListObject карты к данным](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  
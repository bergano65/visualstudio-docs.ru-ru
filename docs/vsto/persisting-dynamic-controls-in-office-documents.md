---
title: Сохранение динамических элементов управления в документах Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 48b2cc1402243bfedb7b22280b4a161235cb9957
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863517"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Сохранение динамических элементов управления в документах Office

Элементы управления, добавленные во время выполнения, не сохраняются при сохранении и закрытии документа или книги. Точное поведение элементов управления ведущего приложения и Windows Forms различается. В обоих случаях можно добавить в решение код для повторного создания элементов управления при повторном открытии документа.

Элементы управления, добавляемые в документы во время выполнения, называются *динамическими элементами управления*. Дополнительные сведения о динамических элементах управления см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>Сохранение элементов управления ведущего приложения в документе

Если сохранить и закрыть документ, все динамические элементы управления ведущего приложения будут удалены из документа. Останутся только базовые собственные объекты Office. Например, элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> превращается в <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName>. Собственные объекты Office не подключены к событиям элементов управления ведущего приложения и не имеют функций привязки к данным элемента управления ведущего приложения.

В следующей таблице перечислены собственные объекты Office, которые остаются в документе после всех типов элементов управления ведущего приложения.

|Тип элемента управления ведущего приложения|Тип собственного объекта Office|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Повторно создать динамические элементы управления при открытии документов

Динамические элементы управления ведущего приложения можно повторно создавать вместо существующих собственных элементов управления при каждом открытии документа пользователем. Создание элементов управления ведущего приложения при открытии документа имитирует поведение, на которое могут рассчитывать пользователи.

Для повторного создания элемента управления ведущего приложения для Word, или <xref:Microsoft.Office.Tools.Excel.NamedRange> или <xref:Microsoft.Office.Tools.Excel.ListObject> управления ведущего приложения для Excel, используйте `Add` \< *класс элемента управления*> метод <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> или <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> объекта. Используйте метод, имеющий параметр для собственного объекта Office.

Например, если вы хотите создать элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> из существующего собственного <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> при открытии документа, используйте метод <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> и передайте существующий <xref:Microsoft.Office.Interop.Excel.ListObject>. В следующем примере кода показано, как сделать это в проекте уровня документа для Excel. Код повторно создает динамический <xref:Microsoft.Office.Tools.Excel.ListObject> , основанный на существующем <xref:Microsoft.Office.Interop.Excel.ListObject> с именем `MyListObject` в классе `Sheet1` .

[!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
[!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]

### <a name="re-create-chart"></a>Повторное создание диаграммы

Для повторного создания <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> размещения элемента управления, необходимо сначала удалить собственный <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>, а затем повторно создать <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> с помощью <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> метод. Существует не `Add` \< *класс элемента управления*> метод, который позволяет создавать новый <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> на основе существующего <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>.

Если вы сначала не удалить собственный <xref:Microsoft.Office.Interop.Excel.Chart>, а затем создается вторая диаграмма-дубликат при повторном создании <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName>.

## <a name="persist-windows-forms-controls-in-documents"></a>Сохранение элементов управления Windows Forms в документах

Если сохранить и закрыть документ, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] автоматически удалит все динамически созданные элементы управления Windows Forms из документа. При этом на уровне проектов уровня документа и надстроек VSTO поведение отличается.

В настройках уровня документа элементы управления и их базовые оболочки ActiveX (которые используются для размещения элементов управления в документе) удаляются при следующем открытии документа. Признаков присутствия элементов управления не остается.

В надстройках VSTO элементы управления удаляются, но оболочки ActiveX остаются в документе. Когда пользователь откроет документ в следующий раз, оболочки ActiveX останутся видны. В Excel оболочки ActiveX содержат изображения элементов управления в том виде, как они выглядели в момент последнего сохранения документа. В Word оболочки ActiveX невидимы, пока пользователь не щелкнет их. После этого в них отображается пунктирная линия, представляющая границы элементов управления. Существует несколько способов удаления оболочек ActiveX. Дополнительные сведения см. в разделе [удаление оболочек ActiveX в надстройке](#removingActiveX).

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>Повторно создать элементы управления Windows Forms при открытии документов

Удаленные элементы управления Windows Forms можно повторно создать при повторном открытии документа. Для этого в решении следует выполнять следующие задачи.

1.  Сохранять информацию о размере, расположении и состоянии элементов управления при сохранении или закрытии документа. В настройке уровня документа можно сохранить данные в кэш данных в документе. В надстройке VSTO можно сохранить данные пользовательской XML-части в документе.

2.  Повторно создавать элементы управления в событии, которое возникает при открытии документа. В проекте уровня документа это можно сделать в обработчиках `Sheet`*n*`_Startup` или `ThisDocument_Startup` . В проекте надстройки VSTO это можно сделать в обработчиках событий <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> или <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

###  <a name="removingActiveX"></a> Удаление оболочек ActiveX в надстройке

При добавлении динамических элементов управления Windows Forms в документы с помощью надстройки VSTO, оболочки ActiveX для элементов управления можно не появлялись в документе при следующем открытии одним из следующих способов.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>Удаление оболочек ActiveX при открытии документа

Чтобы удалить все оболочки ActiveX, вызовите метод `GetVstoObject` для создания ведущего элемента <xref:Microsoft.Office.Interop.Word.Document> или <xref:Microsoft.Office.Interop.Excel.Workbook>, который представляет открытый документ. Например, чтобы удалить все оболочки ActiveX из документа Word, можно вызвать метод `GetVstoObject` для создания ведущего элемента объекта <xref:Microsoft.Office.Interop.Word.Document>, который передается в обработчик событий для события <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.

Эта процедура полезна, когда известно, что документ будет открываться только на компьютерах, где установлена надстройка VSTO. Если документ может быть передан другим пользователям, у которых не установлена надстройка VSTO, рекомендуется удалять элементы управления перед закрытием документа.

В следующем примере кода показано, как вызвать метод `GetVstoObject` при открытии документа.

[!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
[!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]

Несмотря на то что `GetVstoObject` метод используется в основном для создания нового ведущего элемента во время выполнения, этот метод также очищает все оболочки ActiveX из документа при первом вызове для определенного документа. Дополнительные сведения об использовании `GetVstoObject` метод, см. в разделе [документов расширения Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

Если Ваша надстройка VSTO создает динамические элементы управления при открытии документа, Ваша надстройка VSTO вызовет `GetVstoObject` метод как часть процесса создания элементов управления. В этом случае не нужно добавлять отдельный вызов метода `GetVstoObject`, чтобы удалить все оболочки ActiveX.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Удаление динамических элементов управления перед закрытием документа

Надстройка VSTO может явным образом удалить все динамические элементы управления из документа до его закрытия. Эта процедура полезна для документов, передаваемых другим пользователям, у которых не установлена надстройка VSTO.

В следующем примере кода демонстрируется удаление всех элементов управления Windows Forms из документа Word при его закрытии.

[!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
[!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]

## <a name="see-also"></a>См. также

- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)

---
title: "Сохранение динамических элементов управления в документы Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 10f5840b085ce55485734c9287972a743859c3ef
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="persisting-dynamic-controls-in-office-documents"></a>Сохранение динамических элементов управления в документах Office
  Элементы управления, добавленные во время выполнения, не сохраняются при сохранении и закрытии документа или книги. Точное поведение элементов управления ведущего приложения и Windows Forms различается. В обоих случаях можно добавить в решение код для повторного создания элементов управления при повторном открытии документа.  
  
 Элементы управления, добавляемые в документы во время выполнения, называются *динамическими элементами управления*. Дополнительные сведения о динамических элементах управления см. в разделе [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="persisting-host-controls-in-the-document"></a>Сохранение элементов управления ведущего приложения в документе  
 Если сохранить и закрыть документ, все динамические элементы управления ведущего приложения будут удалены из документа. Останутся только базовые собственные объекты Office. Например, элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject> превращается в <xref:Microsoft.Office.Interop.Excel.ListObject>. Собственные объекты Office не подключены к событиям элементов управления ведущего приложения и не имеют функций привязки к данным элемента управления ведущего приложения.  
  
 В следующей таблице перечислены собственные объекты Office, которые остаются в документе после всех типов элементов управления ведущего приложения.  
  
|Тип элемента управления ведущего приложения|Тип собственного объекта Office|  
|-----------------------|-------------------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### <a name="re-creating-dynamic-host-controls-when-documents-are-opened"></a>Повторное создание динамических элементов управления ведущего приложения при открытии документов  
 Динамические элементы управления ведущего приложения можно повторно создавать вместо существующих собственных элементов управления при каждом открытии документа пользователем. Создание элементов управления ведущего приложения при открытии документа имитирует поведение, на которое могут рассчитывать пользователи.  
  
 Для повторного создания элемента управления ведущего приложения для Word или <xref:Microsoft.Office.Tools.Excel.NamedRange> или <xref:Microsoft.Office.Tools.Excel.ListObject> элемента управления ведущего приложения для Excel, используйте `Add` \< *класса элемента управления*> метод <xref:Microsoft.Office.Tools.Excel.ControlCollection> или <xref:Microsoft.Office.Tools.Word.ControlCollection> объекта. Используйте метод, имеющий параметр для собственного объекта Office.  
  
 Например, если вы хотите создать элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject> из существующего собственного <xref:Microsoft.Office.Interop.Excel.ListObject> при открытии документа, используйте метод <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> и передайте существующий <xref:Microsoft.Office.Interop.Excel.ListObject>. В следующем примере кода показано, как сделать это в проекте уровня документа для Excel. Код повторно создает динамический <xref:Microsoft.Office.Tools.Excel.ListObject> , основанный на существующем <xref:Microsoft.Office.Interop.Excel.ListObject> с именем `MyListObject` в классе `Sheet1` .  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]  
  
### <a name="re-creating-charts"></a>Повторное создание диаграмм  
 Для повторного создания элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.Chart> необходимо сначала удалить собственный <xref:Microsoft.Office.Interop.Excel.Chart>, а затем повторно создать <xref:Microsoft.Office.Tools.Excel.Chart> с помощью метода <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> или <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> . Имеется не `Add` \< *класса элемента управления*> метод, который позволяет создавать новый <xref:Microsoft.Office.Tools.Excel.Chart> на основе существующего <xref:Microsoft.Office.Interop.Excel.Chart>.  
  
 Если сначала не удалить собственный <xref:Microsoft.Office.Interop.Excel.Chart>, при повторном создании <xref:Microsoft.Office.Tools.Excel.Chart>будет создана вторая диаграмма-дубликат.  
  
## <a name="persisting-windows-forms-controls-in-documents"></a>Сохранение элементов управления Windows Forms в документах  
 Если сохранить и закрыть документ, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] автоматически удалит все динамически созданные элементы управления Windows Forms из документа. При этом на уровне проектов уровня документа и надстроек VSTO поведение отличается.  
  
 В настройках уровня документа элементы управления и их базовые оболочки ActiveX (которые используются для размещения элементов управления в документе) удаляются при следующем открытии документа. Признаков присутствия элементов управления не остается.  
  
 В надстройках VSTO элементы управления удаляются, но оболочки ActiveX остаются в документе. Когда пользователь откроет документ в следующий раз, оболочки ActiveX останутся видны. В Excel оболочки ActiveX содержат изображения элементов управления в том виде, как они выглядели в момент последнего сохранения документа. В Word оболочки ActiveX невидимы, пока пользователь не щелкнет их. После этого в них отображается пунктирная линия, представляющая границы элементов управления. Существует несколько способов удаления оболочек ActiveX. Дополнительные сведения см. в разделе [Удаление оболочек ActiveX в надстройке](#removingActiveX).  
  
### <a name="re-creating-windows-forms-controls-when-documents-are-opened"></a>Повторное создание динамических элементов управления Windows Forms при открытии документов  
 Удаленные элементы управления Windows Forms можно повторно создать при повторном открытии документа. Для этого в решении следует выполнять следующие задачи.  
  
1.  Сохранять информацию о размере, расположении и состоянии элементов управления при сохранении или закрытии документа. В настройке уровня документа эти данные можно сохранить в кэше данных в документе. В надстройке VSTO эти данные можно сохранить в пользовательской XML-части документа.  
  
2.  Повторно создавать элементы управления в событии, которое возникает при открытии документа. В проекте уровня документа это можно сделать в обработчиках `Sheet`*n*`_Startup` или `ThisDocument_Startup` . В проекте надстройки VSTO это можно сделать в обработчиках событий <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> или <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .  
  
###  <a name="removingActiveX"></a> Удаление оболочек ActiveX в надстройке  
 Если динамические элементы управления Windows Forms добавляются в документы с помощью надстройки VSTO, появление оболочек ActiveX для элементов управления при следующем открытии документа можно предотвратить следующими способами.  
  
#### <a name="removing-activex-wrappers-when-the-document-is-opened"></a>Удаление оболочек ActiveX при открытии документа  
 Чтобы удалить все оболочки ActiveX, вызовите метод GetVstoObject для создания ведущего элемента для <xref:Microsoft.Office.Interop.Word.Document> или <xref:Microsoft.Office.Interop.Excel.Workbook> , представляющий открытый документ. Например, чтобы удалить все оболочки ActiveX из документа Word, можно вызвать метод GetVstoObject для создания ведущего элемента для <xref:Microsoft.Office.Interop.Word.Document> объекта, передаваемого в обработчик событий для <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> события.  
  
 Эта процедура полезна, когда известно, что документ будет открываться только на компьютерах, где установлена надстройка VSTO. Если документ может быть передан другим пользователям, у которых не установлена надстройка VSTO, рекомендуется удалять элементы управления перед закрытием документа.  
  
 В следующем примере кода показано, как вызвать метод GetVstoObject при открытии документа.  
  
 [!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
 [!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]  
  
 Несмотря на то, что метод GetVstoObject используется в основном для создания нового ведущего элемента во время выполнения, этот метод также удаляет все оболочки ActiveX из документа при первом вызове для определенного документа. Дополнительные сведения о том, как использовать метод GetVstoObject см. в разделе [расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Обратите внимание, что если Ваша надстройка VSTO создает динамические элементы управления при открытии документа, Ваша надстройка VSTO уже вызвала метод GetVstoObject как часть процесса создания элементов управления. Необходимо добавлять отдельный вызов метода GetVstoObject, чтобы удалить все оболочки ActiveX в этом сценарии.  
  
#### <a name="removing-the-dynamic-controls-before-the-document-is-closed"></a>Удаление динамических элементов управления до закрытия документа  
 Надстройка VSTO может явным образом удалить все динамические элементы управления из документа до его закрытия. Эта процедура полезна для документов, передаваемых другим пользователям, у которых не установлена надстройка VSTO.  
  
 В следующем примере кода демонстрируется удаление всех элементов управления Windows Forms из документа Word при его закрытии.  
  
 [!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
 [!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]  
  
## <a name="see-also"></a>См. также  
 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  
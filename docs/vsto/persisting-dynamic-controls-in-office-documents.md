---
title: "Сохранение динамических элементов управления в документах Office"
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
  - "Документы Office [разработка решений Office в Visual Studio], элементы управления Windows Forms"
  - "документы Office [разработка решений Office в Visual Studio], элементы управления ведущего приложения"
  - "Элементы управления [разработка решений Office в Visual Studio], сохранение в документе"
  - "Элементы управления Windows Forms [разработка решений Office в Visual Studio], сохранение в документе"
  - "документы [разработка решений Office в Visual Studio], элементы управления Windows Forms"
  - "документы [разработка решений Office в Visual Studio], элементы управления ведущего приложения"
  - "Элементы управления ведущего приложения [разработка решений Office в Visual Studio], сохранение в документе"
ms.assetid: 200352d1-66aa-4156-9ecd-6fd8792974cd
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Сохранение динамических элементов управления в документах Office
  Элементы управления, добавленные во время выполнения, не сохраняются при сохранении и закрытии документа или книги. Точное поведение элементов управления ведущего приложения и Windows Forms различается. В обоих случаях можно добавить в решение код для повторного создания элементов управления при повторном открытии документа.  
  
 Элементы управления, добавляемые в документы во время выполнения, называются *динамическими элементами управления*. Дополнительные сведения о динамических элементах управления см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Сохранение элементов управления ведущего приложения в документе  
 Если сохранить и закрыть документ, все динамические элементы управления ведущего приложения будут удалены из документа. Останутся только базовые собственные объекты Office. Например, элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject> превращается в <xref:Microsoft.Office.Interop.Excel.ListObject>. Собственные объекты Office не подключены к событиям элементов управления ведущего приложения и не имеют функций привязки к данным элемента управления ведущего приложения.  
  
 В следующей таблице перечислены собственные объекты Office, которые остаются в документе после всех типов элементов управления ведущего приложения.  
  
|Тип элемента управления ведущего приложения|Тип собственного объекта Office|  
|-------------------------------------------------|-------------------------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### Повторное создание динамических элементов управления ведущего приложения при открытии документов  
 Динамические элементы управления ведущего приложения можно повторно создавать вместо существующих собственных элементов управления при каждом открытии документа пользователем. Создание элементов управления ведущего приложения при открытии документа имитирует поведение, на которое могут рассчитывать пользователи.  
  
 Для повторного создания элемента управления ведущего приложения в Word или Excel \(<xref:Microsoft.Office.Tools.Excel.NamedRange> или <xref:Microsoft.Office.Tools.Excel.ListObject> соответственно\) используйте метод `Add`\<*класс\_элемента\_управления*\> для объекта <xref:Microsoft.Office.Tools.Excel.ControlCollection> или <xref:Microsoft.Office.Tools.Word.ControlCollection>. Используйте метод, имеющий параметр для собственного объекта Office.  
  
 Например, если вы хотите создать элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject> из существующего собственного <xref:Microsoft.Office.Interop.Excel.ListObject> при открытии документа, используйте метод <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> и передайте существующий <xref:Microsoft.Office.Interop.Excel.ListObject>. В следующем примере кода показано, как сделать это в проекте уровня документа для Excel. Код повторно создает динамический <xref:Microsoft.Office.Tools.Excel.ListObject>, основанный на существующем <xref:Microsoft.Office.Interop.Excel.ListObject> с именем `MyListObject` в классе `Sheet1`.  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/Sheet1.vb#6)]  
  
### Повторное создание диаграмм  
 Для повторного создания элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.Chart> необходимо сначала удалить собственный <xref:Microsoft.Office.Interop.Excel.Chart>, а затем повторно создать <xref:Microsoft.Office.Tools.Excel.Chart> с помощью метода <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> или <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A>. Не существует метода `Add`\<*класс\_элемента\_управления*\>, который бы позволял создать новый <xref:Microsoft.Office.Tools.Excel.Chart> на основе существующего <xref:Microsoft.Office.Interop.Excel.Chart>.  
  
 Если сначала не удалить собственный <xref:Microsoft.Office.Interop.Excel.Chart>, при повторном создании <xref:Microsoft.Office.Tools.Excel.Chart> будет создана вторая диаграмма\-дубликат.  
  
## Сохранение элементов управления Windows Forms в документах  
 Если сохранить и закрыть документ, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] автоматически удалит все динамически созданные элементы управления Windows Forms из документа. При этом на уровне проектов уровня документа и надстроек VSTO поведение отличается.  
  
 В настройках уровня документа элементы управления и их базовые оболочки ActiveX \(которые используются для размещения элементов управления в документе\) удаляются при следующем открытии документа. Признаков присутствия элементов управления не остается.  
  
 В надстройках VSTO элементы управления удаляются, но оболочки ActiveX остаются в документе. Когда пользователь откроет документ в следующий раз, оболочки ActiveX останутся видны. В Excel оболочки ActiveX содержат изображения элементов управления в том виде, как они выглядели в момент последнего сохранения документа. В Word оболочки ActiveX невидимы, пока пользователь не щелкнет их. После этого в них отображается пунктирная линия, представляющая границы элементов управления. Существует несколько способов удаления оболочек ActiveX. Дополнительные сведения см. в разделе [Удаление оболочек ActiveX в надстройке](#removingActiveX).  
  
### Повторное создание динамических элементов управления Windows Forms при открытии документов  
 Удаленные элементы управления Windows Forms можно повторно создать при повторном открытии документа. Для этого в решении следует выполнять следующие задачи.  
  
1.  Сохранять информацию о размере, расположении и состоянии элементов управления при сохранении или закрытии документа. В настройке уровня документа эти данные можно сохранить в кэше данных в документе. В надстройке VSTO эти данные можно сохранить в пользовательской XML\-части документа.  
  
2.  Повторно создавать элементы управления в событии, которое возникает при открытии документа. В проекте уровня документа это можно сделать в обработчиках `Sheet`*n*`_Startup` или `ThisDocument_Startup`. В проекте надстройки VSTO это можно сделать в обработчиках событий <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> или <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
###  <a name="removingActiveX"></a> Удаление оболочек ActiveX в надстройке  
 Если динамические элементы управления Windows Forms добавляются в документы с помощью надстройки VSTO, появление оболочек ActiveX для элементов управления при следующем открытии документа можно предотвратить следующими способами.  
  
#### Удаление оболочек ActiveX при открытии документа  
 Чтобы удалить все оболочки ActiveX, вызовите метод GetVstoObject для создания ведущего элемента <xref:Microsoft.Office.Interop.Word.Document> или <xref:Microsoft.Office.Interop.Excel.Workbook>, который представляет открытый документ. Например, чтобы удалить все оболочки ActiveX из документа Word, можно вызвать метод GetVstoObject для создания ведущего элемента объекта <xref:Microsoft.Office.Interop.Word.Document>, который передается в обработчик событий для события <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
 Эта процедура полезна, когда известно, что документ будет открываться только на компьютерах, где установлена надстройка VSTO. Если документ может быть передан другим пользователям, у которых не установлена надстройка VSTO, рекомендуется удалять элементы управления перед закрытием документа.  
  
 В следующем примере кода показано, как вызвать метод GetVstoObject при открытии документа.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#11)]
 [!code-vb[Trin_WordAddInDynamicControls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#11)]  
  
 Хотя метод GetVstoObject в основном используется для создания нового ведущего элемента во время выполнения, этот метод также удаляет все оболочки ActiveX из документа при первом вызове для определенного документа. Дополнительные сведения об использовании метода GetVstoObject см. в разделе [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Обратите внимание, что если надстройка VSTO создает динамические элементы управления при открытии документа, она уже вызвала метод GetVstoObject в ходе создания элементов управления. В этом случае не нужно добавлять отдельный вызов метода GetVstoObject, чтобы удалить все оболочки ActiveX.  
  
#### Удаление динамических элементов управления до закрытия документа  
 Надстройка VSTO может явным образом удалить все динамические элементы управления из документа до его закрытия. Эта процедура полезна для документов, передаваемых другим пользователям, у которых не установлена надстройка VSTO.  
  
 В следующем примере кода демонстрируется удаление всех элементов управления Windows Forms из документа Word при его закрытии.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#10)]
 [!code-vb[Trin_WordAddInDynamicControls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#10)]  
  
## См. также  
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  
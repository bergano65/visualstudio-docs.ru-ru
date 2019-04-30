---
title: Обновление проектов Excel и Word, которые переносятся на .NET Framework 4 или .NET Framework 4.5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fd80f4a72151fdebb3f0445024963a65db981e63
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436476"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Обновление проектов Excel и Word, которые переносятся на .NET Framework 4 или .NET Framework 4.5
  Если у вас есть проект Excel или Word, в котором используется любой из следующих компонентов, необходимо изменить код, если целевая версия .NET Framework меняется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю:

- [Методы GetVstoObject и HasVstoObject](#GetVstoObject)

- [Созданные классы в проектах уровня документа](#generatedclasses)

- [Элементы управления Windows Forms в документах](#winforms)

- [События элементов управления содержимым Word](#ccevents)

- [Классы OLEObject и OLEControl](#ole)

- [Свойство Controls.Item(Object)](#itemproperty)

- [Коллекции, производные от CollectionBase](#collections)

  Необходимо также удалить `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` и ссылки на `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` класс из проектов Excel, которые переориентируются [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии. Visual Studio не удаляет этот атрибут или ссылка на класс для вас.

## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Удаление атрибута ExcelLocale1033 из проектов Excel
 `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` Был удален из той части Visual Studio 2010 Tools для Office runtime, которая используется для решений, предназначенных [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии. Среда CLR в [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и более поздней версии всегда передает код языка 1033 объектной модели Excel. Вы больше не можете использовать этот атрибут, чтобы отключить такое поведение. Дополнительные сведения см. в разделе [Глобализация и локализация решений Excel](../vsto/globalization-and-localization-of-excel-solutions.md).

### <a name="to-remove-the-excellocale1033attribute"></a>Удаление ExcelLocale1033Attribute

1. Откройте проект в Visual Studio, а затем откройте **Обозреватель решений**.

2. В узле **Свойства** (для C#) или **Мой проект** (для Visual Basic) дважды щелкните файл кода AssemblyInfo, чтобы открыть его в редакторе кода.

    > [!NOTE]
    > В проектах Visual Basic для просмотра файла с кодом AssemblyInfo необходимо нажать кнопку **Показать все файлы** в **обозревателе решений** .

3. Найдите `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` и удалите его из файла или закомментируйте его.

    ```vb
    <Assembly: ExcelLocale1033Proxy(True)>
    ```

    ```csharp
    [assembly: ExcelLocale1033Proxy(true)]
    ```

## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Удалить ссылку на класс ExcelLocal1033Proxy
 Проекты, созданные с помощью набора средств Microsoft Visual Studio 2005 для системы Microsoft Office, создают экземпляр объекта <xref:Microsoft.Office.Interop.Excel.Application> Excel с помощью класса `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy`. Этот класс был удален из той части Visual Studio 2010 Tools для Office runtime, которая используется для решений, предназначенных [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии. Таким образом, необходимо удалить или закомментировать строку кода, которая ссылается на этот класс.

### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Удаление ссылки на класс ExcelLocal1033Proxy

1. Откройте проект в Visual Studio, а затем откройте **Обозреватель решений**.

2. В **обозревателе решений**, откройте контекстное меню для *ThisAddin.cs* (для C#) или *ThisAddin.vb* (для Visual Basic), а затем выберите **Просмотр кода** .

3. В редакторе кода в области `VSTO generated code` удалите или закомментируйте следующую строку кода.

    ```vb
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)

    ```

    ```csharp
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);

    ```

## <a name="GetVstoObject"></a> Обновление кода, использующего методы GetVstoObject и HasVstoObject
 В проектах, предназначенных для .NET Framework 3.5, методы `GetVstoObject` и `HasVstoObject` доступны как методы расширения в одном из следующих собственных объектов проекта: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet> или <xref:Microsoft.Office.Interop.Excel.ListObject>. При вызове этих методов передавать параметр не требуется. В следующем примере кода демонстрируется использование метода GetVstoObject в надстройке VSTO для Word, ориентированном на .NET Framework 3.5.

```vb
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()
```

```csharp
Microsoft.Office.Tools.Word.Document vstoDocument =
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();
```

 В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, необходимо изменить код для доступа к этим методам одним из следующих способов:

- Вы по-прежнему можете обратиться к этим методам как к методам расширения в объектах <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>и <xref:Microsoft.Office.Interop.Excel.ListObject> . Однако теперь этим методам необходимо передать объект, возвращаемый свойством `Globals.Factory`.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);
  ```

- Можно также обратиться к этим методам в объекте, который возвращается свойством `Globals.Factory`. При таком доступе к этим методам необходимо передать методу собственный объект, который требуется расширить до метода.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);
  ```

  Дополнительные сведения см. в разделе [документов расширения Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="generatedclasses"></a> Обновление кода, использующего экземпляры созданных классов в проектах уровня документа
 В проектах на уровне документа, ориентированных на .NET Framework 3.5, созданные классы в проектах являются производными от следующих классов в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>

- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>

- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>

  В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, перечисленные выше типы в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] — это интерфейсы, а не классы. Созданные классы в проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, являются производными от приведенных ниже новых классов в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>

- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>

- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>

  Если код в вашем проекте ссылается на экземпляр одного из созданных классов в качестве базового класса, производным от которого он является, необходимо изменить код.

  Например, в проекте книги Excel, ориентированном на .NET Framework 3.5, может присутствовать вспомогательный метод, который выполняет некоторые операции с экземплярами созданных классов `Sheet`*n* в проекте.

```vb
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)
    ' Do something to the worksheet object.
End Sub
```

```csharp
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)
{
    // Do something to the worksheet object.
}
```

 Если изменить целевую платформу на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, необходимо внести одно из следующих изменений в код:

- Измените любой код, который вызывает метод `DoSomethingToSheet` для передачи свойства <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> объекта <xref:Microsoft.Office.Tools.Excel.WorksheetBase> в проекте. Это свойство возвращает объект <xref:Microsoft.Office.Tools.Excel.Worksheet> .

    ```vb
    DoSomethingToSheet(Globals.Sheet1.Base)
    ```

    ```csharp
    DoSomethingToSheet(Globals.Sheet1.Base);
    ```

- Измените параметр метода `DoSomethingToSheet` так, чтобы он принимал объект <xref:Microsoft.Office.Tools.Excel.WorksheetBase> .

    ```vb
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)
        ' Do something to the worksheet object.
    End Sub
    ```

    ```csharp
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)
    {
        // Do something to the worksheet object.
    }
    ```

## <a name="winforms"></a> Обновление кода, использующего элементы управления Windows Forms в документах
 Необходимо добавить **с помощью** (C#) или **Imports** выражения (Visual Basic) для <xref:Microsoft.Office.Tools.Excel> или <xref:Microsoft.Office.Tools.Word> пространства имен в начало любого файла кода, использующего свойство элементов управления для добавления Windows Элемент управления Forms в документ или лист.

 В проектах, ориентированных на .NET Framework 3.5, методы, добавляющие элементы управления Windows Forms (такие как `AddButton`), определяются в классах <xref:Microsoft.Office.Tools.Excel.ControlCollection> и <xref:Microsoft.Office.Tools.Word.ControlCollection>.

 В проектах, предназначенных [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, эти методы являются методами расширения, доступные на свойства элементов управления. Чтобы использовать эти методы расширения, файл кода, в котором используются методы, должен содержать оператор **using** и **Imports** для пространства имен <xref:Microsoft.Office.Tools.Excel> и <xref:Microsoft.Office.Tools.Word> . Этот оператор создается автоматически в новых проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии. Однако этот оператор не добавляется автоматически в проектах, ориентированных на .NET Framework 3.5, поэтому вам необходимо добавить его при изменении целевой платформы проекта.

 Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="ccevents"></a> Обновление кода, который обрабатывает события элементов управления содержимым Word
 В проектах, ориентированных на .NET Framework 3.5, события элементов управления содержимым Word обрабатываются универсальным делегатом <xref:System.EventHandler%601> . В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, эти события обрабатываются другими делегатами.

 В следующей таблице перечислены элементы управления содержимым Word и делегаты, связанные с ними в проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии.

|событие|Делегат, используемый в проектах для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и более поздних версий|
|-----------| - |
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|

## <a name="ole"></a> Обновление кода, использующего классы классы OLEObject и OLEControl
 В проектах, ориентированных на .NET Framework 3.5, можно добавить пользовательские элементы управления (например, элементы управления Windows Forms) в документ или на лист с помощью классов `Microsoft.Office.Tools.Excel.OLEObject` и `Microsoft.Office.Tools.Word.OLEControl`.

 В проектах, ориентированных на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, эти классы заменены интерфейсами <xref:Microsoft.Office.Tools.Excel.ControlSite> и <xref:Microsoft.Office.Tools.Word.ControlSite> . Вам необходимо изменить код, который ссылается на `Microsoft.Office.Tools.Excel.OLEObject` и `Microsoft.Office.Tools.Word.OLEControl` так, чтобы он ссылался на <xref:Microsoft.Office.Tools.Excel.ControlSite> и <xref:Microsoft.Office.Tools.Word.ControlSite>. За исключением новых имен, эти элементы управления ведут себя так же, как и в проектах, ориентированных на .NET Framework 3.5.

 Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="itemproperty"></a> Обновление кода, использующего свойство Controls.Item(Object)
 В проектах, ориентированных на .NET Framework 3.5, можно использовать свойство Item(Object) Microsoft.Office.Tools.Word.Document.Controls или `Microsoft.Office.Tools.Excel.Worksheet.Controls` коллекции, чтобы определить, имеет ли документ или лист указанный элемент управления.

 В проектах, предназначенных [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, свойство Item(Object) был удален из этих коллекций. Чтобы определить, содержит ли документ или лист указанный элемент управления, используйте метод Contains(System.Object) <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> или <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> коллекции вместо этого.

 Дополнительные сведения о коллекции элементов управления документов и листов см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="collections"></a> Обновление кода, использующего коллекции, производные от CollectionBase
 В проектах, ориентированных на .NET Framework 3.5, некоторые типы коллекций в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] являются производными от <xref:System.Collections.CollectionBase> класс, например `Microsoft.Office.Tools.SmartTagCollection`, `Microsoft.Office.Tools.Excel.ControlCollection`, и `Microsoft.Office.Tools.Word.ControlCollection`.

 В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и более поздней версии, эти типы коллекций теперь представляют собой интерфейсы, не являющиеся производными от <xref:System.Collections.CollectionBase>. Некоторые члены в этих типах коллекций, такие как <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>и <xref:System.Collections.CollectionBase.InnerList%2A>, больше не доступны.

## <a name="see-also"></a>См. также
- [Перенос решений Office на .NET Framework 4 или более поздней версии](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Элементы управления содержимым](../vsto/content-controls.md)
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)

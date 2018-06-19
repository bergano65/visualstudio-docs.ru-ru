---
title: Тестирование приложений SharePoint с помощью закодированных тестов пользовательского интерфейса в Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 5a23ed3a56c0d4b8daf8086e07ae04206c52ac4a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979455"
---
# <a name="test-sharepoint-applications-with-coded-ui-tests"></a>Тестирование приложений SharePoint с помощью закодированных тестов пользовательского интерфейса

Включение закодированных тестов пользовательского интерфейса в приложение SharePoint дает возможность проверки того, является ли все приложение, включая элементы управления пользовательского интерфейса, правильным. Можно также использовать закодированные тесты пользовательского интерфейса для проверки значений и логики в пользовательском интерфейсе.

Дополнительные сведения о преимуществах закодированных тестов пользовательского интерфейса см. в статье [Использование модели автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md).

**Требования**

- Visual Studio Enterprise

## <a name="create-a-coded-ui-test-for-a-sharepoint-app"></a>Создание закодированного теста пользовательского интерфейса для приложения SharePoint

[Создание закодированных тестов пользовательского интерфейса](../test/use-ui-automation-to-test-your-code.md) для приложений SharePoint происходит таким же способом, что и создание тестов для других типов приложений. Запись и воспроизведение поддерживаются для всех элементов управления в интерфейсе веб-редактирования. Интерфейс для выбора категорий и веб-частей — стандартные веб-элементы управления.

![веб-части SharePoint](../test/media/cuit_sharepoint.png)

> [!NOTE]
> В случае записи действия необходимо проверить действия перед созданием кода. Поскольку существует несколько расширений функциональности, связанных с указателем мыши, оно включено по умолчанию. Следите за тем, чтобы удалить повторные наведения на основе закодированных тестов пользовательского интерфейса. Это можно сделать, отредактировав код для теста или с помощью [Редактора закодированных тестов пользовательского интерфейса](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="test-office-controls-within-a-sharepoint-app"></a>Тестирование элементов управления Office в приложении SharePoint

Чтобы включить автоматизацию для некоторых веб-частей Office в приложении SharePoint, необходимо внести некоторые небольшие изменения в код.

> [!NOTE]
> Тестирование элементов управления Visio и PowerPoint в приложении SharePoint не поддерживается.

### <a name="excel-cell-controls"></a>Элементы управления ячейки Excel

Для включения элемента управления ячейками Excel необходимо внести некоторые изменения в код закодированных тестов пользовательского интерфейса.

> [!WARNING]
> Вставка текста в любую ячейку Excel, а затем действие клавишей со стрелкой не запишется правильно. Используйте мышь для выделения ячеек.

Если происходит запись действий в пустой ячейке, необходимо изменить код, дважды щелкнув по ячейке и выполнив набор операций с текстом. Это необходимо, поскольку щелчок по ячейке, за которым следует любое действие клавиатуры, активирует `textarea` внутри ячейки. Простая запись `setvalue` в пустой ячейке вызовет поиск `editbox` , которого не существует, пока по ячейке не щелкнули. Пример:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

Запись действий в непустой ячейке получается более сложной, так как при добавлении текста в ячейку новый элемент управления \<div> добавляется в качестве дочернего элемента ячейки. Новый элемент управления \<div> содержит только что введенный текст. Записывающему устройству необходимо записать действия в новый элемент управления \<div>; но оно не может это сделать, так как новый элемент управления \<div> не существует, пока не закончен ввод теста. Необходимо вручную внести следующие изменения кода, чтобы уладить эту проблему.

1. В инициализации ячейки измените основные свойства `RowIndex` и `ColumnIndex` :

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Найдите дочерний элемент `HtmlDiv` ячейки:

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }
    ```

3. Добавьте код для действия двойного щелчка мышью по `HtmlDiv`:

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. Добавьте код, чтобы вставить текст в `TextArea`:

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ``

## See also

- [Use UI Automation To Test Your Code](../test/use-ui-automation-to-test-your-code.md)
- [Create SharePoint Solutions](/office-dev/office-dev/create-sharepoint-solutions)
- [Verifying and Debugging SharePoint Code](/office-dev/office-dev/verifying-and-debugging-sharepoint-code)
- [Building and Debugging SharePoint Solutions](/office-dev/office-dev/building-and-debugging-sharepoint-solutions)
- [Profiling the Performance of SharePoint Applications](/office-dev/office-dev/profiling-the-performance-of-sharepoint-applications)

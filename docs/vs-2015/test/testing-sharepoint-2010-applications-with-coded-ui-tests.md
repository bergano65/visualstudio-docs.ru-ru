---
title: Тестирование приложений SharePoint 2010 с помощью закодированных тестов пользовательского интерфейса | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: 32
ms.author: gewarren
manager: douge
ms.openlocfilehash: 346362a6812882bd795b6180ac735e51f13e3530
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303762"
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Тестирование приложений SharePoint 2010 с помощью закодированных тестов пользовательского интерфейса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Включение закодированных тестов пользовательского интерфейса в приложение SharePoint дает возможность проверки того, является ли все приложение, включая элементы управления пользовательского интерфейса, правильным. Можно также использовать закодированные тесты пользовательского интерфейса для проверки значений и логики в пользовательском интерфейсе.  
  
 **Требования**  
  
-   Visual Studio Enterprise  
  
## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Что еще следует знать о кодированных тестах пользовательского интерфейса?  
 См. дополнительные сведения о преимуществах использования закодированных тестов пользовательского интерфейса разделах об [использовании автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md) и [тестировании для непрерывной поставки с использованием Visual Studio 2012 (глава 5, посвященная автоматизации системных тестов)](http://go.microsoft.com/fwlink/?LinkID=255196).  
  
 **Примечания**  
  
-   ![Необходимый компонент](../test/media/prereq.png "Prereq") Тесты закодированного пользовательского интерфейса для приложений SharePoint поддерживаются только при наличии SharePoint 2010.  
  
-   ![Необходимый компонент](../test/media/prereq.png "Prereq") Элементы управления Visio и PowerPoint 2010 в приложении SharePoint не поддерживаются.  
  
## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>Создание закодированного теста пользовательского интерфейса для приложения SharePoint  
 [Создание закодированных тестов пользовательского интерфейса](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) для приложений SharePoint 2010 происходит таким же способом, что и создание тестов для других типов приложений. Запись и воспроизведение поддерживаются для всех элементов управления в интерфейсе веб-редактирования. Интерфейс для выбора категорий и веб-частей — стандартные веб-элементы управления.  
  
 ![Веб-части SharePoint](../test/media/cuit-sharepoint.png "CUIT_SharePoint")  
  
> [!NOTE]
>  В случае записи действия необходимо проверить действия перед созданием кода. Поскольку существует несколько расширений функциональности, связанных с указателем мыши, оно включено по умолчанию. Следите за тем, чтобы удалить повторные наведения на основе закодированных тестов пользовательского интерфейса. Это можно сделать, отредактировав код для теста или с помощью [Редактора закодированных тестов пользовательского интерфейса](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>Включение тестирования элементов управления Office 2010 в приложении SharePoint  
 Чтобы включить автоматизацию для некоторых веб-частей Office 2010 в приложении SharePoint, необходимо внести некоторые небольшие изменения в код.  
  
> [!WARNING]
>  Элементы управления Visio и PowerPoint 2010 не поддерживаются.  
  
### <a name="excel-2010-cell-controls"></a>Элементы управления ячейки Excel 2010  
 Для включения элемента управления ячейками Excel необходимо внести некоторые изменения в код закодированных тестов пользовательского интерфейса.  
  
> [!WARNING]
>  Вставка текста в любую ячейку Excel, а затем действие клавишей со стрелкой не запишется правильно. Используйте мышь для выделения ячеек.  
  
 Если происходит запись действий в пустой ячейке, необходимо изменить код, дважды щелкнув по ячейке и выполнив набор операций с текстом. Это необходимо, поскольку щелчок по ячейке, за которым следует любое действие клавиатуры, активирует `textarea` внутри ячейки. Простая запись `setvalue` в пустой ячейке вызовет поиск `editbox` , которого не существует, пока по ячейке не щелкнули. Пример:  
  
```csharp  
Mouse.DoubliClick(uiItemCell,new Point(31,14));  
uiGridKeyboardInputEdit.Text=value;  
```  
  
 Запись действий в непустой ячейке получается более сложной, так как при добавлении текста в ячейку новый элемент управления \<div> добавляется в качестве дочернего элемента ячейки. Новый элемент управления \<div> содержит только что введенный текст. Записывающему устройству необходимо записать действия в новый элемент управления \<div>; но оно не может это сделать, так как новый элемент управления \<div> не существует, пока не закончен ввод теста. Необходимо вручную внести следующие изменения кода, чтобы уладить эту проблему.  
  
1.  В инициализации ячейки измените основные свойства `RowIndex` и `ColumnIndex` :  
  
    ```csharp  
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";   
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";  
    ```  
  
2.  Найдите дочерний элемент `HtmlDiv` ячейки:  
  
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
  
3.  Добавьте код для действия двойного щелчка мышью по `HtmlDiv`:  
  
    ```csharp  
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )  
    ```  
  
4.  Добавьте код, чтобы вставить текст в `TextArea`:  
  
    ```csharp  
    uIGridKeyboardInputEdit.Text = value; }  
    ```  
  
## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Включение кодированных тестов пользовательского интерфейса веб-частей Silverlight в приложении SharePoint 2010  
 Тестирование Silverlight не поддерживается в Visual Studio 2012 и более поздних версий. Однако если вы хотите тестировать веб-части Silverlight в своем приложении SharePoint 2010, можно установить отдельный подключаемый модуль Silverlight из коллекции Visual Studio.  
  
#### <a name="setting-up-your-machine"></a>Настройка компьютера  
  
1.  Убедитесь, что установлен Visual Studio 2012.1 или более поздней версии.  
  
2.  Установите [Подключаемый модуль тестов пользовательского интерфейса Microsoft Visual Studio для Silverlight](http://visualstudiogallery.msdn.microsoft.com/28312a61-9451-451a-990c-c9929b751eb4).  
  
3.  Установите [Fiddler](http://www.fiddler2.com/fiddler2/). Это средство для перехватывания и регистрации HTTP-трафика.  
  
4.  Загрузите [проект fiddlerXap](http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-components-postattachments/00-10-36-48-70/FiddlerXapProxy.zip). Распакуйте его, выполните его сборку и запустите скрипт "CopySLHelper.bat" для установки вспомогательной библиотеки DLL, необходимой для тестирования веб-части Silverlight во время использования инструмента Fiddler.  
  
 После настройки компьютера, чтобы начать тестирование приложения SharePoint 2010 с веб-частями Silverlight, выполните следующие действия.  
  
#### <a name="testing-silverlight-web-parts"></a>Тестирование веб-частей Silverlight  
  
1.  Запустите Fiddler.  
  
2.  Очистите кэш браузера. Это необходимо, поскольку XAP-файл, содержащий вспомогательную библиотеку модели автоматизации пользовательского интерфейса Silverlight, обычно кэшируется. Следует убедиться, что измененный XAP-файл будет замечен, поэтому рекомендуется очистить кэш браузера.  
  
3.  Откройте веб-страницу.  
  
4.  Запустите запись и сгенерируйте код как для обычного тестирования веб-приложения.  
  
5.  Необходимо убедиться, что созданный код ссылается на Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll.  
  
     Дополнительные сведения см. в разделе [Тестирование пользовательского интерфейса SharePoint 2010 с помощью Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
### <a name="blogs"></a>Блоги  
 [Тестирование пользовательского интерфейса SharePoint 2010 с помощью Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
 [Основные сведения о логике поиска для элементов управления Silverlight в редакторе закодированных тестов пользовательского интерфейса](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/understanding-the-search-logic-for-silverlight-controls-in-coded-ui-test.aspx)  
  
 [Получение свойства элемента управления Silverlight](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/fetching-property-of-a-silverlight-control.aspx)  
  
 [Индекс содержимого для закодированных тестов пользовательского интерфейса](http://blogs.msdn.com/b/mathew_aniyan/archive/2010/02/11/content-index-for-coded-ui-test.aspx)  
  
### <a name="guidance"></a>Руководство  
 [Тестирование при непрерывной поставке с использованием Visual Studio 2012, глава 5, "Автоматизация системных тестов"](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="forum"></a>Форум  
 [Блог по Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=254496)  
  
## <a name="see-also"></a>См. также  
 [Использование модели автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md)   
 [Применение веб-тестов производительности и нагрузочных тестов для приложений SharePoint 2010 и 2013](http://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54)   
 [Создание решений SharePoint](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631)   
 [Проверка и отладка кода SharePoint](http://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c)   
 [Построение и отладка решений SharePoint](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae)   
 [Профилирование производительности приложений SharePoint](http://msdn.microsoft.com/library/61ae02e7-3f37-4230-bae1-54a498c2fae8)




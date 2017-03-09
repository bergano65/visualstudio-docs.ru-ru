---
title: "Пример надстройки Excel для закодированного тестирования пользовательского интерфейса | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "закодированные тесты пользовательского интерфейса, пример надстройки Excel"
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "mlearned"
manager: "douge"
---
# Пример надстройки Excel для закодированного тестирования пользовательского интерфейса
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Этот пример надстройки для [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] разработан специально для поддержки закодированных тестов пользовательского интерфейса листов Excel, записываемых и запускаемых в Visual Studio Enterprise. Надстройка создается с помощью Visual Studio Tools for Office.  
  
 Дополнительные сведения о создании надстройки Excel см. в разделе [Пошаговое руководство. Создание первой надстройки VSTO для Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md) или выполните поиск «надстройка Excel» в библиотеке MSDN.  
  
 Хотя надстройка Excel не является основным предметом этой документации по расширению закодированных тестов пользовательского интерфейса для Excel, несколько комментариев могут пригодиться.  
  
 Далее приведены важные части этой надстройки.  
  
-   Класс `ThisAddIn` управляет каналом удаленного взаимодействия .NET между `ExcelUICommunicator` и [Пример расширения закодированного теста пользовательского интерфейса для Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx`  — сертификат безопасности для тестирования надстройки.  
  
-   Класс `ExcelUICommunicator` реализует интерфейс `IExcelUICommunication`.  
  
## Класс ThisAddIn  
 Большая часть этого класса фактически создается средствами Visual Studio Tools for Office в файле `ThisAddIn.Designer.cs` при создании проекта надстройки Excel.  
  
 Члены, которые необходимо реализовать, — это обработчики событий `ThisAddIn_Startup()` и `ThisAddIn_Shutdown()`.  Они используются, чтобы инициализировать или закрыть канал удаленного взаимодействия .NET, используемый `ExcelUICommunicator`.  
  
## ExcelCodedUIAddinHelper\_TemporaryKey.pfx  
 Этот файл содержит временный сертификат безопасности, создаваемый Visual Studio Tools for Office, и предоставляет сборке надстройки разрешение на работу в процессе Excel для тестирования надстройки и расширения.  Следует удалить этот сертификат и либо создать новый на вкладке **Подписывание** окна проекта **Свойства**, либо подключить собственный сертификат тестирования.  
  
## Класс ExcelUICommunicator  
 Этот класс реализует интерфейс `IExcelUITestCommunication` и получает запрошенные сведения о пользовательском интерфейсе из объектной модели Excel.  Дополнительные сведения см. в разделе [Пример интерфейса коммуникатора в Excel](../test/sample-excel-communicator-interface.md).  
  
## См. также  
 [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Пошаговое руководство. Создание первой надстройки VSTO для Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md)   
 [Office and SharePoint Development](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)
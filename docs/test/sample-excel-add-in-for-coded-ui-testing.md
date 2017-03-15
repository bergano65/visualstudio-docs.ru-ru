---
title: "Пример надстройки Excel для закодированного тестирования пользовательского интерфейса | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 16
ms.author: mlearned
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 52b0394f0e52b8b7b640611253dcef693b4eca3c
ms.lasthandoff: 02/22/2017

---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Пример надстройки Excel для закодированного тестирования пользовательского интерфейса
Этот пример надстройки для [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] разработан специально для поддержки закодированных тестов пользовательского интерфейса листов Excel, записываемых и запускаемых в Visual Studio Enterprise. Надстройка создается с помощью набора средств Visual Studio для Office.  
  
 Дополнительные сведения о создании надстройки Excel см. в статье [Walkthrough: Creating Your First VSTO Add-in for Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) (Пошаговое руководство. Создание первой надстройки уровня приложения для Excel) или выполните поиск "надстройка Excel" в библиотеке MSDN.  
  
 Хотя надстройка Excel не является основным предметом этой документации по расширению закодированных тестов пользовательского интерфейса для Excel, несколько комментариев могут пригодиться.  
  
 Далее приведены важные части этой надстройки.  
  
-   Класс `ThisAddIn` управляет каналом удаленного взаимодействия .NET между `ExcelUICommunicator` и [примером расширения закодированных тестов пользовательского интерфейса для Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx` — сертификат безопасности для тестирования надстройки.  
  
-   Класс `ExcelUICommunicator` реализует интерфейс `IExcelUICommunication`.  
  
## <a name="thisaddin-class"></a>Класс ThisAddIn  
 Большая часть этого класса фактически создается набором средств Visual Studio для Office в файле `ThisAddIn.Designer.cs` при создании проекта надстройки Excel.  
  
 Члены, которые необходимо реализовать, — это обработчики событий `ThisAddIn_Startup()` и `ThisAddIn_Shutdown()`. Они используются, чтобы инициализировать или закрыть канал удаленного взаимодействия .NET, используемый `ExcelUICommunicator`.  
  
## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx  
 Этот файл содержит временный сертификат безопасности, создаваемый набором средств Visual Studio для Office, и предоставляет сборке надстройки разрешение на работу в процессе Excel для тестирования надстройки и расширения. Следует удалить этот сертификат и либо создать новый на вкладке **Подписывание** окна проекта **Свойства**, либо подключить собственный сертификат тестирования.  
  
## <a name="exceluicommunicator-class"></a>Класс ExcelUICommunicator  
 Этот класс реализует интерфейс `IExcelUITestCommunication` и получает запрошенные сведения о пользовательском интерфейсе из объектной модели Excel. Дополнительные сведения см. в статье [Sample Excel Communicator Interface](../test/sample-excel-communicator-interface.md) (Пример интерфейса Excel Communicator).  
  
## <a name="see-also"></a>См. также  
 [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Walkthrough: Creating Your First VSTO Add-in for Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)  (Пошаговое руководство. Создание первой надстройки VSTO для Excel)  
 [Office and SharePoint Development](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio) (Разработка приложений Office и SharePoint)

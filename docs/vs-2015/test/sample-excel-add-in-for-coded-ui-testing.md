---
title: Пример надстройки Excel для закодированного тестирования пользовательского интерфейса | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 18
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0f0b4211b51940564041fab5777d6594168e1329
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568996"
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Пример надстройки Excel для закодированного тестирования пользовательского интерфейса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [пример надстройки Excel для закодированного тестирования пользовательского интерфейса](https://docs.microsoft.com/visualstudio/test/sample-excel-add-in-for-coded-ui-testing).  
  
Этот пример надстройки для [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] разработан специально для поддержки закодированных тестов пользовательского интерфейса листов Excel, записываемых и запускаемых в Visual Studio Enterprise. Надстройка создается с помощью набора средств Visual Studio для Office.  
  
 Дополнительные сведения о создании надстройки Excel см. в статье [Walkthrough: Creating Your First VSTO Add-in for Excel](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) (Пошаговое руководство. Создание первой надстройки уровня приложения для Excel) или выполните поиск "надстройка Excel" в библиотеке MSDN.  
  
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
 [Walkthrough: Creating Your First VSTO Add-in for Excel](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)  (Пошаговое руководство. Создание первой надстройки VSTO для Excel)  
 [Office and SharePoint Development](http://msdn.microsoft.com/library/2ddec047-263a-4901-a54c-a15fc8472329) (Разработка приложений Office и SharePoint)




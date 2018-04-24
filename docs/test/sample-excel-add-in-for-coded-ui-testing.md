---
title: Пример надстройки Excel для закодированного тестирования пользовательского интерфейса | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: aee4f7bcf827fc7d42b9c885d78b83df1ea54fd3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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

- [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
- [Пошаговое руководство. Создание первой надстройки VSTO для Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)
- [Office and SharePoint Development](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio) (Разработка приложений Office и SharePoint)

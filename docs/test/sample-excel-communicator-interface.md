---
title: "Пример интерфейса коммуникатора в Excel | Документы Майкрософт"
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: bc372077b36680e3b0dc8ec0ad482f8df0c52609
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="sample-excel-communicator-interface"></a>Пример интерфейса коммуникатора в Excel
Пример интерфейса `IExcelUICommunication` используется в объекте `ExcelUICommunicator` в проекте `ExcelAddIn`.

## <a name="iexceluicommunication-interface"></a>Интерфейс IExcelUICommunication
 Этот интерфейс определяет точки взаимодействия между расширением `CodedUIExtension`, выполняющимся в процессе закодированного теста пользовательского интерфейса, и надстройкой `ExcelCodedUIAddIn`, выполняющейся в процессе [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

 Сборка `ExcelCodedUIAddinHelper` содержит класс `ExcelUICommunicator`, являющийся производным от этого интерфейса и использующий для обработки методов объектную модуль Excel.

 Некоторые методы получают запрашиваемую информацию из Excel, а затем создают и возвращают один из информационных объектов, например объект `CellInformation`.

 Другие методы используют полученный информационный объект, находят соответствующий элемент управления в Excel и выполняют определенный процесс с помощью этого элемента управления. Например, метод `ScrollIntoView` прокручивает лист, чтобы стала видимой нужная ячейка.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>Взаимодействие между CodedUIExtensibilitySample и ExcelCodedUIAddinHelper
 Сборка `ExcelCodedUIAddinHelper` выполняется в процессе Excel и содержит класс `UICommunicator`, реализующий интерфейс `IExcelUITestCommunication` и получающий или задающий необходимую информацию непосредственно в пользовательском интерфейсе Excel.

 Сборка `CodedUIExtensibilitySample` выполняется в процессе закодированного теста пользовательского интерфейса Visual Studio. Эта сборка содержит класс `Communicator`, открывающий канал удаленного взаимодействия .NET и предоставляющий свойство `Instance`, которое использует интерфейс `IExcelUICommunication` для использования объекта `UICommunicator` в сборке `ExcelCodedUIAddinHelper` для передачи запросов и информационных объектов, например объекта `CellInformation`, между двумя сборками.

## <a name="see-also"></a>См. также

- [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
- [Пример надстройки Excel для закодированного тестирования пользовательского интерфейса](../test/sample-excel-add-in-for-coded-ui-testing.md)
- [Пример расширения закодированного теста пользовательского интерфейса для Excel](../test/sample-coded-ui-test-extension-for-excel.md)

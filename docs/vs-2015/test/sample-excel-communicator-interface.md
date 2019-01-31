---
title: Пример интерфейса коммуникатора в Excel | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 42da15899bb9bab6388d32c87132796eff768d7e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800021"
---
# <a name="sample-excel-communicator-interface"></a>Пример интерфейса коммуникатора в Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пример интерфейса `IExcelUICommunication` используется в объекте `ExcelUICommunicator` в проекте `ExcelAddIn`.  
  
## <a name="iexceluicommunication-interface"></a>Интерфейс IExcelUICommunication  
 Этот интерфейс определяет точки взаимодействия между расширением `CodedUIExtension`, выполняющимся в процессе закодированного теста пользовательского интерфейса, и надстройкой `ExcelCodedUIAddIn`, выполняющейся в процессе [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
 Сборка `ExcelCodedUIAddinHelper` содержит класс `ExcelUICommunicator`, являющийся производным от этого интерфейса и использующий для обработки методов объектную модуль Excel.  
  
 Некоторые методы получают запрашиваемую информацию из Excel, а затем создают и возвращают один из информационных объектов, например объект `CellInformation`.  
  
 Другие методы используют полученный информационный объект, находят соответствующий элемент управления в Excel и выполняют определенный процесс с помощью этого элемента управления. Например, метод `ScrollIntoView` прокручивает лист, чтобы стала видимой нужная ячейка.  
  
## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>Взаимодействие между CodedUIExtensibilitySample и ExcelCodedUIAddinHelper  
 Сборка `ExcelCodedUIAddinHelper` выполняется в процессе Excel и содержит класс `UICommunicator`, реализующий интерфейс `IExcelUITestCommunication` и получающий или задающий необходимую информацию непосредственно в пользовательском интерфейсе Excel.  
  
 Сборка `CodedUIExtensibilitySample` выполняется в процессе закодированного теста пользовательского интерфейса Visual Studio. Эта сборка содержит класс `Communicator`, открывающий канал удаленного взаимодействия .NET и предоставляющий свойство `Instance`, которое использует интерфейс `IExcelUICommunication` для использования объекта `UICommunicator` в сборке `ExcelCodedUIAddinHelper` для передачи запросов и информационных объектов, например объекта `CellInformation`, между двумя сборками.  
  
## <a name="see-also"></a>См. также раздел  
 [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Пример надстройки Excel для закодированного тестирования пользовательского интерфейса](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Пример расширения закодированного теста пользовательского интерфейса для Excel](../test/sample-coded-ui-test-extension-for-excel.md)

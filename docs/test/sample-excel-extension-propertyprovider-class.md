---
title: Пример расширения Excel. Класс PropertyProvider
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e4a1e96fc666275d83cf0f32edf00f0fc2f6c03c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Пример расширения Excel. Класс PropertyProvider
Этот внутренний класс расширяет класс <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> и обеспечивает свойства для элементов [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)], чтобы можно было записывать и воспроизводить тесты пользовательского интерфейса.

## <a name="getcontrolsupportlevel-method"></a>Метод GetControlSupportLevel
 Метод <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> возвращает число, обозначающее уровень поддержки, обеспечиваемый поставщиком свойства для указанного элемента управления. Чем выше это значение, тем лучше поставщик свойств поддерживает элемент управления. В данном случае метод проверяет значение свойства <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> указанного элемента управления. Если значение равняется Excel, а свойство <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> задает `CellElement`, метод возвращает наибольшее значение; в противном случае он возвращает ноль, что означает, что поддержка не предоставляется.

## <a name="getpropertynames-method"></a>Метод GetPropertyNames
 Возвращает словарь имен и дескрипторов свойств для поддерживаемых свойств элемента управления "Ячейка" Excel.

## <a name="getpropertydescriptor-method"></a>Метод GetPropertyDescriptor
 Этот метод вызывается платформой тестирования для получения предварительно определенного дескриптора свойства для указанного имени свойства.

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>Методы GetPropertyValue и SetPropertyValue
 Метод `GetPropertyValue` использует класс `Communicator` этого расширения, чтобы возвращать значение свойства из Excel. Метод `SetPropertyValue` использует класс <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> и компонент `Communicator`, чтобы задавать значение свойства. Эти методы вызываются платформой тестирования.

## <a name="code-generation-customization-methods"></a>Методы настройки создания кода
 Для данного расширения эти методы не реализованы. Поэтому они возвращают значение `null` или вызывают исключение <xref:System.NotImplementedException>.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
- [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

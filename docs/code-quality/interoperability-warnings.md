---
title: предупреждения взаимодействия
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9736eabf741219dbdba1f8bbd206429145c91c72
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535814"
---
# <a name="interoperability-warnings"></a>предупреждения взаимодействия

Предупреждения взаимодействия поддерживают взаимодействие с клиентами COM.

## <a name="in-this-section"></a>Содержание

| Правило | Описание |
| - | - |
| [CA1400: необходимо наличие точек входа P/Invoke](../code-quality/ca1400.md) | Открытый или защищенный метод, помеченный атрибутом System.Runtime.InteropServices.DllImportAttribute. Не удается найти неуправляемую библиотеку либо не удается сопоставить метод функции в библиотеке. |
| [CA1401: методы P/Invoke не должны быть видимыми](../code-quality/ca1401.md) | Открытый или защищенный метод в открытом типе имеет атрибут System. Runtime. InteropServices. DllImportAttribute (также реализуется с помощью ключевого слова Declare в Visual Basic). Такие методы не следует делать видимыми. |
| [CA1402: не используйте перегрузки в интерфейсах, видимых в COM](../code-quality/ca1402.md) | Когда перегруженные методы предоставляются клиентам COM, сохраняется имя только первой перегрузки метода. Последующие перегрузки переименовываются уникальным образом путем добавления к имени символа подчеркивания (_) и целого числа, соответствующего порядку объявления перегрузки. |
| [CA1403: типы с автомакетом не должны быть видимыми для COM](../code-quality/ca1403.md) | Тип значения, видимый для COM, помечен с помощью атрибута System. Runtime. InteropServices. StructLayoutAttribute, установленного в LayoutKind. Auto. Макет этих типов может изменяться между версиями .NET, что приведет к нарушению работы клиентов COM, которые предполагают наличие определенного макета. |
| [CA1404: вызывайте GetLastError сразу после P/Invoke](../code-quality/ca1404.md) | Выполняется вызов метода Marshal. GetLastWin32Error или эквивалентной функции [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError, а предыдущий вызов не является методом вызова неуправляемого кода. |
| [CA1405: базовые типы, относящиеся к типу видимых COM-клиенту, должны быть видимыми для COM](../code-quality/ca1405.md) | Тип, видимый для модели COM, наследует от типа, который не является видимым для COM. |
| [CA1406: не используйте аргументы Int64 для клиентов Visual Basic 6](../code-quality/ca1406.md) | Visual Basic 6 COM-клиентов не может получить доступ к 64-разрядным целым числам. |
| [CA1407: не используйте статические члены в видимых COM типах](../code-quality/ca1407.md) | Модель COM не поддерживает статические методы. |
| [CA1408: не используйте AutoDual ClassInterfaceType](../code-quality/ca1408.md) | Типы, использующие сдвоенный интерфейс, позволяют клиентам выполнять привязку к определенному макету интерфейса. Все изменения в будущей версии макета типа и в базовых типах приведут к нарушению работы COM-клиентов, связанных с интерфейсом. По умолчанию, если атрибут ClassInterfaceAttribute не указан, используется только диспетчерский интерфейс. |
| [CA1409: видимые COM-типы должны быть создаваемыми](../code-quality/ca1409.md) | Ссылочный тип, который специально помечен как видимый для модели COM, содержит открытый параметризованный конструктор, но не содержит открытого конструктора по умолчанию (без параметров). COM-клиенты не могут создавать объекты типа, не содержащего открытый конструктор по умолчанию. |
| [CA1410: методы регистрации для COM-клиента должны быть соответствующими](../code-quality/ca1410.md) | Тип объявляет метод, помеченный с помощью атрибута <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>, но не объявляет метод, помеченный атрибутом <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>, или наоборот. |
| [CA1411: методы регистрации для COM-клиента не должны быть видимыми](../code-quality/ca1411.md) | Метод, помеченный атрибутом System. Runtime. InteropServices. Комрегистерфунктионаттрибуте или атрибутом System. Runtime. InteropServices. Комунрегистерфунктионаттрибуте, является внешним видимым. |
| [CA1412: помечайте интерфейсы ComSource как IDispatch](../code-quality/ca1412.md) | Тип помечен атрибутом System.Runtime.InteropServices.ComSourceInterfacesAttribute, однако по крайней мере один из указанных интерфейсов не помечен атрибутом System.Runtime.InteropServices.InterfaceTypeAttribute, значение которого равно ComInterfaceType.InterfaceIsIDispatch. |
| [CA1413: избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413.md) | Не являющиеся общедоступными поля экземпляров типов значений, отображаемых для модели COM, отображаются для COM-клиентов. Проверьте содержимое полей на наличие сведений, к которым не должен предоставляться доступ или которые могут оказать непреднамеренное воздействие на разработку или безопасность. |
| [CA1414: пометьте логические аргументы P/Invoke с помощью атрибута MarshalAs](../code-quality/ca1414.md) | Логический тип данных имеет несколько представлений в неуправляемом коде. |
| [CA1415: правильно объявляйте методы P/Invoke](../code-quality/ca1415.md) | Это правило выполняет поиск объявлений методов вызова неуправляемого кода, предназначенных для [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] функций, имеющих указатель на параметр структуры OVERLAPPED, и соответствующий управляемый параметр не является указателем на структуру <xref:System.Threading.NativeOverlapped?displayProperty=fullName>. |

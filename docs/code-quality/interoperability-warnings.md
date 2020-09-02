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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74bffffa2b4f95aeab20438199bb19693a1a3b94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235125"
---
# <a name="interoperability-warnings"></a>предупреждения взаимодействия

Предупреждения взаимодействия поддерживают взаимодействие с клиентами COM.

## <a name="in-this-section"></a>в этом разделе

| Правило | Описание |
| - | - |
| [CA1400: должны существовать точки входа P/Invoke](../code-quality/ca1400.md) | Открытый или защищенный метод, помеченный атрибутом System.Runtime.InteropServices.DllImportAttribute. Не удается найти неуправляемую библиотеку либо не удается сопоставить метод функции в библиотеке. |
| [CA1401: методы P/Invoke не должны быть видимыми](../code-quality/ca1401.md) | Открытый или защищенный метод в открытом типе имеет атрибут System.Runtime.InteropServices.DllImportAttribute (также реализованное ключевым словом Declare в Visual Basic). Такие методы не следует делать видимыми. |
| [CA1402. Избегайте перегрузок в видимых COM-интерфейсах](../code-quality/ca1402.md) | Когда перегруженные методы предоставляются клиентам COM, сохраняется имя только первой перегрузки метода. Последующие перегрузки переименовываются уникальным образом путем добавления к имени символа подчеркивания (_) и целого числа, соответствующего порядку объявления перегрузки. |
| [CA1403. Типы с автомакетом не должны быть видимыми для COM](../code-quality/ca1403.md) | Тип значения, видимый для COM, помечен с помощью атрибута System. Runtime. InteropServices. StructLayoutAttribute, установленного в LayoutKind. Auto. Макет этих типов может изменяться между версиями .NET, что приведет к нарушению работы клиентов COM, которые предполагают наличие определенного макета. |
| [CA1404: вызов GetLastError сразу после P/Invoke](../code-quality/ca1404.md) | Выполняется вызов метода Marshal. GetLastWin32Error или эквивалентной [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] функции GetLastError, а предыдущий вызов не является методом вызова неуправляемого кода. |
| [CA1405. Базовые типы, относящиеся к типу, видимому для COM, должны быть видимыми для COM](../code-quality/ca1405.md) | Тип, видимый для модели COM, наследует от типа, который не является видимым для COM. |
| [CA1406. Не используйте аргументы Int64 для клиентов Visual Basic 6](../code-quality/ca1406.md) | COM-клиенты VisualBasic 6 не могут получать доступ к 64-разрядным целым числам. |
| [CA1407. Не используйте статические члены в типах, видимых для COM](../code-quality/ca1407.md) | Модель COM не поддерживает статические методы. |
| [CA1408. Не используйте тип AutoDual ClassInterfaceType](../code-quality/ca1408.md) | Типы, использующие сдвоенный интерфейс, позволяют клиентам выполнять привязку к определенному макету интерфейса. Все изменения в будущей версии макета типа и в базовых типах приведут к нарушению работы COM-клиентов, связанных с интерфейсом. По умолчанию, если атрибут ClassInterfaceAttribute не указан, используется только диспетчерский интерфейс. |
| [CA1409. Видимые для COM типы должны быть создаваемыми](../code-quality/ca1409.md) | Ссылочный тип, который специально помечен как видимый для модели COM, содержит открытый параметризованный конструктор, но не содержит открытого конструктора по умолчанию (без параметров). COM-клиенты не могут создавать объекты типа, не содержащего открытый конструктор по умолчанию. |
| [CA1410. Методы регистрации COM должны быть согласованными](../code-quality/ca1410.md) | Тип объявляет метод, помеченный с помощью <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> атрибута, но не объявляет метод, помеченный <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> атрибутом, или наоборот. |
| [CA1411. Методы регистрации COM не должны быть видимыми](../code-quality/ca1411.md) | Метод, помеченный атрибутом System. Runtime. InteropServices. Комрегистерфунктионаттрибуте или атрибутом System. Runtime. InteropServices. Комунрегистерфунктионаттрибуте, является внешним видимым. |
| [CA1412. Пометьте интерфейсы ComSource как IDispatch](../code-quality/ca1412.md) | Тип помечен атрибутом System.Runtime.InteropServices.ComSourceInterfacesAttribute, однако по крайней мере один из указанных интерфейсов не помечен атрибутом System.Runtime.InteropServices.InterfaceTypeAttribute, значение которого равно ComInterfaceType.InterfaceIsIDispatch. |
| [CA1413. Не используйте неоткрытые поля в типах значений, видимых для COM](../code-quality/ca1413.md) | Не являющиеся общедоступными поля экземпляров типов значений, отображаемых для модели COM, отображаются для COM-клиентов. Проверьте содержимое полей на наличие сведений, к которым не должен предоставляться доступ или которые могут оказать непреднамеренное воздействие на разработку или безопасность. |
| [CA1414: помечайте логические аргументы P/Invoke с помощью MarshalAs](../code-quality/ca1414.md) | Логический тип данных имеет несколько представлений в неуправляемом коде. |
| [CA1415: правильно объявляйте P/Invoke](../code-quality/ca1415.md) | Это правило выполняет поиск объявлений методов вызова неуправляемого кода, предназначенных [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] для функций, имеющих указатель на параметр структуры OVERLAPPED, и соответствующий управляемый параметр не является указателем на <xref:System.Threading.NativeOverlapped?displayProperty=fullName> структуру. |
| [CA1417: не используйте `OutAttribute` в строковых параметрах для P/Invoke](../code-quality/ca1417.md) | Строковые параметры, передаваемые по значению, `OutAttribute` могут дестабилизировать среду выполнения, если строка является интернированной строкой. |
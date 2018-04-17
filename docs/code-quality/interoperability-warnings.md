---
title: Предупреждения взаимодействия | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f1046c07a55e683141f8f6879a45e4e55b3f3f9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="interoperability-warnings"></a>предупреждения взаимодействия
Предупреждения взаимодействия поддерживает взаимодействие с COM-клиентам.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Правило|Описание|  
|----------|-----------------|  
|[: CA1400 точек входа P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Открытый или защищенный метод, помеченный атрибутом System.Runtime.InteropServices.DllImportAttribute. Не удается найти неуправляемую библиотеку либо не удается сопоставить метод функции в библиотеке.|  
|[CA1401: методы P/Invoke не должны быть видимыми](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Открытый или защищенный метод в открытом типе имеет атрибут System.Runtime.InteropServices.DllImportAttribute (также реализован с помощью ключевого слова Declare в Visual Basic). Такие методы не следует делать видимыми.|  
|[CA1402: не используйте перегрузки в интерфейсах, видимых в COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Когда перегруженные методы предоставляются клиентам COM, сохраняется имя только первой перегрузки метода. Последующие перегрузки переименовываются уникальным образом путем добавления к имени символа подчеркивания (_) и целого числа, соответствующего порядку объявления перегрузки.|  
|[CA1403: типы с автомакетом не должны быть видимыми для COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Видимый для модели COM тип значения помечается атрибутом System.Runtime.InteropServices.StructLayoutAttribute, имеющим значение LayoutKind.Auto. Макеты этих типов могут меняться в различных версиях платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], что может привести к нарушению работы клиентов COM, которые ожидают определенного макета.|  
|[CA1404: Вызывайте GetLastError сразу после P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Выполняется вызов метода Marshal.GetLastWin32Error или эквивалентной [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] Функция GetLastError, а непосредственно предшествующий вызов не к платформе вызова метода.|  
|[CA1405: базовые типы, относящиеся к типу видимых COM-клиенту, должны быть видимыми для COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Тип, видимый для модели COM, наследует от типа, который не является видимым для COM.|  
|[CA1406: не используйте аргументы Int64 для клиентов Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Клиенты COM Visual Basic 6 не может получить доступ к 64-разрядных целых чисел.|  
|[CA1407: не используйте статические члены в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Модель COM не поддерживает статические методы.|  
|[CA1408: не используйте AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Типы, использующие сдвоенный интерфейс, позволяют клиентам выполнять привязку к определенному макету интерфейса. Все изменения в будущей версии макета типа и в базовых типах приведут к нарушению работы COM-клиентов, связанных с интерфейсом. По умолчанию, если атрибут ClassInterfaceAttribute не указан, используется только диспетчерский интерфейс.|  
|[CA1409: видимые COM-типы должны быть создаваемыми](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Ссылочный тип, который специально помечен как видимый для модели COM, содержит открытый параметризованный конструктор, но не содержит открытого конструктора по умолчанию (без параметров). COM-клиенты не могут создавать объекты типа, не содержащего открытый конструктор по умолчанию.|  
|[CA1410: методы регистрации для COM-клиента должны быть соответствующими](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Тип объявляет метод, помеченный с помощью <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> атрибута, но не объявляет метод, помеченный с помощью <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> атрибут, или наоборот.|  
|[CA1411: методы регистрации для COM-клиента не должны быть видимыми](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Метод, помеченный атрибутом System.Runtime.InteropServices.ComRegisterFunctionAttribute или атрибутом System.Runtime.InteropServices.ComUnregisterFunctionAttribute видим извне.|  
|[CA1412: помечайте интерфейсы ComSource как IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Тип помечен атрибутом System.Runtime.InteropServices.ComSourceInterfacesAttribute, однако по крайней мере один из указанных интерфейсов не помечен атрибутом System.Runtime.InteropServices.InterfaceTypeAttribute, значение которого равно ComInterfaceType.InterfaceIsIDispatch.|  
|[CA1413: избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Не являющиеся общедоступными поля экземпляров типов значений, отображаемых для модели COM, отображаются для COM-клиентов. Проверьте содержимое полей на наличие сведений, к которым не должен предоставляться доступ или которые могут оказать непреднамеренное воздействие на разработку или безопасность.|  
|[CA1414: Пометьте логические аргументы P/Invoke с помощью атрибута MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Логический тип данных имеет несколько представлений в неуправляемом коде.|  
|[CA1415: Правильно объявляйте методы P/Invoke](../code-quality/ca1415-declare-p-invokes-correctly.md)|Это правило ищет неуправляемого объявления методов, предназначенных для [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] функции, которые имеют указатель на параметр структуры OVERLAPPED, соответствующий управляемый параметр не является указателем на <xref:System.Threading.NativeOverlapped?displayProperty=fullName> структуры.|
---
title: CA1408. Не используйте тип AutoDual ClassInterfaceType
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8711ed43749d7bea2c69cee4dd4cb0f0160996a3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844292"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408. Не используйте тип AutoDual ClassInterfaceType

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Отображается тип объектов модели компонентов (COM) помечен с <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибут `AutoDual` значение <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Описание правила
 Типы, использующие сдвоенный интерфейс, позволяют клиентам выполнять привязку к определенному макету интерфейса. Все изменения в будущей версии макета типа и в базовых типах приведут к нарушению работы COM-клиентов, связанных с интерфейсом. По умолчанию если <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибут не указан, используется интерфейс диспетчеризации.

 Если не указано иное, все открытые неуниверсальные типы являются видимыми для COM; все закрытые и универсальные типы невидимы для модели COM.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените значение <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибут `None` значение <xref:System.Runtime.InteropServices.ClassInterfaceType> и явно определяют интерфейс.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если вы не уверены, что макет типа и его базовых типов не изменится в будущих версиях.

## <a name="example"></a>Пример
 Пример класса, который нарушает правило и повторное объявление класса, чтобы использовать явный интерфейс.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1403: Типы с автомакетом не должны быть видимыми для COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: Помечайте интерфейсы ComSource как IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>См. также

- [Oпределение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)
---
title: CA1408. Не используйте тип AutoDual ClassInterfaceType
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b79483e8703ea297634d0d81d5449c09b58c9fb7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921986"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408. Не используйте тип AutoDual ClassInterfaceType

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Видимый тип модели COM помечен <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибутом, `AutoDual` для которого задано значение <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Описание правила
Типы, использующие сдвоенный интерфейс, позволяют клиентам выполнять привязку к определенному макету интерфейса. Все изменения в будущей версии макета типа и в базовых типах приведут к нарушению работы COM-клиентов, связанных с интерфейсом. По умолчанию, если <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибут не указан, используется интерфейс диспетчеризации.

Если не указано иное, все открытые неуниверсальные типы видимы для COM. все неоткрытые и универсальные типы являются невидимыми для COM.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, измените значение <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибута `None` на значение <xref:System.Runtime.InteropServices.ClassInterfaceType> и явно определите интерфейс.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Не отключайте предупреждение из этого правила, если только не уверены в том, что макет типа и его базовые типы не изменятся в следующей версии.

## <a name="example"></a>Пример
В следующем примере показан класс, нарушающий правило, и повторное объявление класса для использования явного интерфейса.

[!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
[!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Связанные правила
[CA1403 Типы автоматического макета не должны быть видимыми для COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

[CA1412 Помечайте интерфейсы пометьте comsource как IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>См. также

- [Oпределение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)
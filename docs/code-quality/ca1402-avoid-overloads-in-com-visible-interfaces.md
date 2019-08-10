---
title: CA1402. Избегайте перегрузок в видимых COM-интерфейсах
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: aa45a54a994d19b1a04bc0785f21b88dfeef4475
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922123"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402. Избегайте перегрузок в видимых COM-интерфейсах

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Видимый интерфейс модели COM объявляет перегруженные методы.

## <a name="rule-description"></a>Описание правила
Когда перегруженные методы предоставляются клиентам COM, сохраняется имя только первой перегрузки метода. Последующие перегрузки уникально переименовываются путем добавления к имени символа подчеркивания "_" и целого числа, соответствующего порядку объявления перегрузки. Например, рассмотрим следующие методы.

```csharp
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

Эти методы предоставляются клиентам COM следующим образом.

```csharp
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

Visual Basic 6 COM-клиенты не могут реализовывать методы интерфейса с помощью символа подчеркивания в имени.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, переименуйте перегруженные методы, чтобы имена были уникальными. Кроме того, можно сделать интерфейс невидимым для com, изменив уровень [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]доступа на `internal` `Friend` (в) <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> или применив `false`атрибут со значением.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показан интерфейс, нарушающий правило, и интерфейс, соответствующий правилу.

[!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
[!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA1413 Избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407 Избегайте статических членов в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017 Пометка сборок с помощью ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также

- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)
- [Тип данных Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)
---
title: 'CA1402: не используйте перегрузки в интерфейсах, видимых в COM'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11c72fa5d64991931dc6c6d2d5506fd73a7cc59f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: не используйте перегрузки в интерфейсах, видимых в COM
|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Компонент модели объектов (COM) отображается интерфейс объявляет перегруженные методы.

## <a name="rule-description"></a>Описание правила
 Когда перегруженные методы предоставляются клиентам COM, сохраняется имя только первой перегрузки метода. Последующие перегрузки переименовываются уникальным образом путем добавления к имени символа подчеркивания «_» и целого числа, соответствующего порядку объявления перегрузки. Например рассмотрим следующие методы.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 Эти методы предоставляются клиентам COM, следующим образом.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Клиенты COM Visual Basic 6 не могут реализовывать методы интерфейса с помощью символа подчеркивания в имени.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, переименуйте перегруженные методы, чтобы имена были уникальными. Кроме того, сделать интерфейс невидимый для COM, изменив специальные возможности `internal` (`Friend` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) или путем применения <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> атрибуту присвоено значение `false`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано, интерфейс, который нарушает правило и интерфейс, соответствующий этому правилу.

 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1413: избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: не используйте статические члены в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index) [Long-тип данных](/dotnet/visual-basic/language-reference/data-types/long-data-type)
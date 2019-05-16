---
title: CA1402. Не используйте перегрузки в интерфейсах, видимых COM | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: abf6382dfba8b8d9c3cc0ed6ccf90e929afca589
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694965"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402. Избегайте перегрузок в видимых COM-интерфейсах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Компонент модели объектов (COM) отображается интерфейс объявляет перегруженные методы.

## <a name="rule-description"></a>Описание правила
 Когда перегруженные методы предоставляются клиентам COM, сохраняется имя только первой перегрузки метода. Последующие перегрузки переименовываются уникальным образом путем добавления к имени символ подчеркивания «_» и целое число, соответствующего порядку объявления перегрузки. Например рассмотрим следующие методы.

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

 Клиенты COM Visual Basic 6 не могут реализовывать методы интерфейса с помощью подчеркивания в имени.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, переименуйте перегруженные методы, чтобы имена являются уникальными. Кроме того, обеспечивает невидимость интерфейс модели COM, изменяя доступность, чтобы `internal` (`Friend` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) либо путем применения <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> атрибут `false`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В примере показан интерфейс, который нарушает правило и интерфейс, соответствующий этому правилу.

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1413: Избегайте не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Не используйте статические члены в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Пометьте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также
 [Взаимодействие с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [тип данных Long](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)

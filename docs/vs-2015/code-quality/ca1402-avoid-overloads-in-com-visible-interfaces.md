---
title: 'CA1402: Избегайте перегрузок в видимых COM-интерфейсах | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b5c1e3af0e35bf92d72e853948c455893b417998
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534944"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402. Избегайте перегрузок в видимых COM-интерфейсах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый интерфейс модели COM объявляет перегруженные методы.

## <a name="rule-description"></a>Описание правила
 Когда перегруженные методы предоставляются клиентам COM, сохраняется имя только первой перегрузки метода. Последующие перегрузки уникально переименовываются путем добавления к имени символа подчеркивания "_" и целого числа, соответствующего порядку объявления перегрузки. Например, рассмотрим следующие методы.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 Эти методы предоставляются клиентам COM следующим образом.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Visual Basic 6 COM-клиенты не могут реализовывать методы интерфейса с помощью символа подчеркивания в имени.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, переименуйте перегруженные методы, чтобы имена были уникальными. Кроме того, можно сделать интерфейс невидимым для COM, изменив уровень доступа на `internal` ( `Friend` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) или применив <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> атрибут со значением `false` .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан интерфейс, нарушающий правило, и интерфейс, соответствующий правилу.

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1413. Не используйте неоткрытые поля в типах значений, видимых для COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407. Не используйте статические члены в типах, видимых для COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017. Пометьте сборки с помощью ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также:
 Взаимодействие с [типом данных Long](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) [неуправляемого кода](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)

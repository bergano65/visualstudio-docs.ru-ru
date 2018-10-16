---
title: 'CA1008: Перечисляемые должен иметь нулевое значение | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e990bd73bfe8341e1cae617c6d31ad5a705ede27
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49297808"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: перечисляемые типы должны иметь нулевое значение
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое — при появлении предложения добавить **None** значение к перечислению без флага. Критическое — если приглашение переименовать или удалить все значения перечисления.|

## <a name="cause"></a>Причина
 Перечисление без примененного <xref:System.FlagsAttribute?displayProperty=fullName> не определяет член, имеющий значение равно нулю, или перечисление с примененного <xref:System.FlagsAttribute> определяет элемент, имеет нулевое значение, но его имя не является «None» или перечисление определяет несколько нулевым значением элементы.

## <a name="rule-description"></a>Описание правила
 Значение по умолчанию неинициализированного перечисления, так же, как и других типов значений, равно нулю. Перечисление не flags−attributed должно определять член с нулевым значением, таким образом, значение по умолчанию — допустимое значение перечисления. При необходимости, имя члена «None». В противном случае присвойте ноль наиболее часто используемых элементов. Обратите внимание на то, что, по умолчанию, если значение первого элемента перечисления не указано в объявлении, его значение равно нулю.

 Если перечисление с <xref:System.FlagsAttribute> применения определяет член с нулевым значением, его имя должно быть «None», чтобы указать, что значения не заданы в перечислении. С помощью член с нулевым значением, для каких-либо других целях — в отличие от использования <xref:System.FlagsAttribute> в том, что и и или битовые операторы смысла для члена. Это означает, что только одному члену должны назначаться нулевое значение. Обратите внимание, что несколько членов, имеющих нулевое значение появление в перечислении флагами в качестве атрибутов, `Enum.ToString()` возвращает неверные результаты для членов, которые не равны нулю.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила для перечислений без flags−attributed, определите член, имеющий значение равно нулю; Это не критическое изменение. Для атрибутов флаги перечисления, которые определяют член с нулевым значением назовите этот член «None» и удалите любые другие члены, которые имеют нулевое значение; Это критическое изменение.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, за исключением перечислений флагов в качестве атрибутов, ранее поставленных.

## <a name="example"></a>Пример
 В следующем примере показано два перечисления, которые удовлетворяют правилу и перечисления, `BadTraceOptions`, который нарушает правило.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: не следует называть значения перечислений именем "Reserved"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: не добавляйте имя типа перед перечисляемыми значениями](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: хранилище перечислений должно иметь тип Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также
 <xref:System.Enum?displayProperty=fullName>




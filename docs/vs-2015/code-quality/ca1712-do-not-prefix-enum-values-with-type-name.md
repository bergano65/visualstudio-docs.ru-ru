---
title: 'CA1712: не добавлять префиксы к перечисляемым значениям с именем типа | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8c79ed71290d54f97bb4ed143d32095b157e2e3e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669127"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: не добавляйте имя типа перед перечисляемыми значениями
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Перечисление содержит элемент, имя которого начинается с имени типа перечисления.

## <a name="rule-description"></a>Описание правила
 Имена членов перечисления не имеют префикса с именем типа, так как ожидается, что информация о типах должна предоставляться средствами разработки.

 Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает время, необходимое для изучения новой библиотеки программного обеспечения, и повышает уверенность клиентов в том, что библиотека была разработана кем-то, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите префикс имени типа из члена перечисления.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано неправильное именованное перечисление, за которым следует исправленная версия.

 [!code-cpp[FxCop.Naming.EnumValues#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cpp/FxCop.Naming.EnumValues.cpp#1)]
 [!code-csharp[FxCop.Naming.EnumValues#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cs/FxCop.Naming.EnumValues.cs#1)]
 [!code-vb[FxCop.Naming.EnumValues#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/vb/FxCop.Naming.EnumValues.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1711: идентификаторы не должны иметь неверных суффиксов](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.Enum?displayProperty=fullName>

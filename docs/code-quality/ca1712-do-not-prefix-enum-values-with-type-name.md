---
title: CA1712. Не добавляйте имя типа перед перечисляемыми значениями
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e7059f1babd3ef65c44b3e7192229e3bb56f2c6e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971329"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712. Не добавляйте имя типа перед перечисляемыми значениями

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Перечисление содержит член, имя которых начинается с именем типа перечисления.

## <a name="rule-description"></a>Описание правила
 Имена членов перечисления не имеют префикс с именем типа, так как ожидается, сведения о типе предоставляются средствами разработки.

 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает время, необходимое для, чтобы изучать новую библиотеку программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите префикс имени типа из члена перечисления.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Следующий пример показывает следуют исправленное перечисление с неправильным именем.

 [!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
 [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
 [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1711: Идентификаторы не должны иметь неверных суффиксов](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027: СЛЕДУЕТ Помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.Enum?displayProperty=fullName>
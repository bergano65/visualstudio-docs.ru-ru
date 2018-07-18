---
title: 'CA1028: хранилище перечислений должно иметь тип Int32'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0f9dec006f3684259541811e905eaf75a790c3a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900292"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: хранилище перечислений должно иметь тип Int32
|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Базовый тип открытого перечисления не является <xref:System.Int32?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Перечисление является типом значения, которое определяет набор связанных именованных констант. По умолчанию <xref:System.Int32?displayProperty=fullName> для хранения значения константы используется тип данных. Несмотря на то, что вы можете изменить этот базовый тип, он не требуется или рекомендуется для большинства сценариев. Обратите внимание, что нет значительный прирост производительности можно добиться, используя тип данных, который меньше, чем <xref:System.Int32>. Если невозможно использовать тип данных по умолчанию, следует использовать один из общей системы (CLS)-совместимые целочисленные типы <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, или <xref:System.Int64> чтобы убедиться в том, что все значения перечисления могут быть представлены в CLS-совместимых языках программирования.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, если существуют проблемы, связанные с размером и совместимостью, используйте <xref:System.Int32>. Для ситуаций, где <xref:System.Int32> недостаточно велик для хранения значений, используйте <xref:System.Int64>. Если для обеспечения обратной совместимости требуется типу данных меньшего размера, используйте <xref:System.Byte> или <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила только в том случае, если это требуется для проблемах обратной совместимости. В приложениях Несоблюдение этого правила обычно не вызывает проблем. В библиотеках, в которых требуется взаимодействие между языками, Несоблюдение этого правила может неблагоприятно повлиять на пользователей.

## <a name="example-of-a-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В следующем примере показано два перечисления, которые следует использовать рекомендованный базовый тип данных.

### <a name="code"></a>Код
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Пример того, как решения по устранению

### <a name="description"></a>Описание
 В следующем примере предыдущее нарушение устраняется путем изменения базового типа данных для <xref:System.Int32>.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1008: перечисляемые типы должны иметь нулевое значение](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: не следует называть значения перечислений именем "Reserved"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: не добавляйте имя типа перед перечисляемыми значениями](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>См. также
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName> <xref:System.Int32?displayProperty=fullName> <xref:System.Int64?displayProperty=fullName>
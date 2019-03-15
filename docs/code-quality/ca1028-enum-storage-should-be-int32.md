---
title: CA1028. Хранилище перечисляемых типов должно относиться к типу Int32
ms.date: 03/11/2019
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 95e2a8892bb7b52122dd34afa3f300123149bb26
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57871854"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028. Хранилище перечисляемых типов должно относиться к типу Int32

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Базовый тип перечисления не является <xref:System.Int32?displayProperty=fullName>.

По умолчанию это правило считывает только открытые перечисления, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Перечисление является типом значения, которое определяет набор связанных именованных констант. По умолчанию <xref:System.Int32?displayProperty=fullName> для хранения значения константы используется тип данных. Несмотря на то, что вы можете изменить это базовый тип, не требуется или не рекомендуется для большинства сценариев. Нет прирост производительности обеспечивается использованием типом данных, меньше, чем <xref:System.Int32>. Если нельзя использовать тип данных по умолчанию, следует использовать один из распространенных системы языков программирования (CLS)-совместимые целочисленных типов, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, или <xref:System.Int64> чтобы убедиться в том, что все значения перечисления могут быть отображены в CLS-совместимым языков программирования.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, если имеются проблемы с размером и совместимостью, используйте <xref:System.Int32>. Для ситуаций, где <xref:System.Int32> недостаточно велик для хранения значений, используйте <xref:System.Int64>. Если требуется более короткого типа данных обратной совместимости с помощью <xref:System.Byte> или <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Отключайте предупреждение из этого правила, только в том случае, если это требуется для проблемах обратной совместимости. В приложениях сбой в соответствии с этим правилом, обычно не вызывает проблем. В библиотеках, где необходима взаимодействие языков, Несоблюдение этого правила может неблагоприятно повлиять на пользователей.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```
dotnet_code_quality.ca1028.api_surface = private, internal
```

В этой категории (структуры) можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Пример нарушения

В следующем примере показано два перечисления, которые не используют рекомендуемые базовый тип данных.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Пример того, как исправить

В следующем примере устраняется нарушение устраняется путем изменения базового типа данных для <xref:System.Int32>.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA1008: Перечисления должны иметь нулевое значение](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027: СЛЕДУЕТ Помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Не значения перечислений именем «Reserved»](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Не добавляйте префикс в виде значения перечисления с именем типа](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>См. также

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>
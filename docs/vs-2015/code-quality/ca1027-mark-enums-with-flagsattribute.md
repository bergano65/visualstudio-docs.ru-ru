---
title: CA1027. Помечать перечисления атрибутом FlagsAttribute | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6603e0869a9eb7947735c52a4c438b39d64b9140
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157710"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027. Пометьте перечисляемые типы с помощью FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытого перечисления степени двух значений или значений являются комбинацией других значений, которые определены в перечислении, и <xref:System.FlagsAttribute?displayProperty=fullName> атрибут не задан. Снизить число ложных срабатываний, это правило не сообщает о нарушениях для перечислений с непрерывными значениями.

## <a name="rule-description"></a>Описание правила
 Перечисление является типом значения, которое определяет набор связанных именованных констант. Применить <xref:System.FlagsAttribute> к перечислению, когда его именованные константы могут быть объединены осмысленным образом. Например рассмотрим перечисление дней недели в приложении, которое следит за какой день ресурсы доступны. Если доступность каждого ресурса кодируется с помощью перечисления с <xref:System.FlagsAttribute> настоящее любое сочетание дней могут быть представлены. Без атрибута может быть представлен только один день недели.

 Для полей, в которых хранятся комбинируемые перечисления отдельное значение перечисления, обрабатываются как группы битов в поле. Поэтому такие поля, иногда называются *битовые поля*. Для объединения значений перечисления для хранения в битовое поле, используйте логические условные операторы. Чтобы проверить битовое поле, чтобы определить наличие конкретного значения перечисления, используйте логические операторы. Для битовое поле для хранения и извлечения значений объединенного перечисления правильно каждое значение, которое определено в перечислении необходимо степенью двух. Если это не так, логические операторы не смогут извлечь отдельное значение перечисления, которые хранятся в поле.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте <xref:System.FlagsAttribute> к перечислению.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, если не хотите, чтобы быть в виде комбинируемых значения перечисления.

## <a name="example"></a>Пример
 В следующем примере `DaysEnumNeedsFlags` является перечислением, который соответствует требованиям по использованию <xref:System.FlagsAttribute>, но не поддерживает его. `ColorEnumShouldNotHaveFlag` Перечисление не имеет значения, являющиеся степенями двух, но неправильно указывает <xref:System.FlagsAttribute>. Это нарушает правило [CA2217: Не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2217: Не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также
 <xref:System.FlagsAttribute?displayProperty=fullName>

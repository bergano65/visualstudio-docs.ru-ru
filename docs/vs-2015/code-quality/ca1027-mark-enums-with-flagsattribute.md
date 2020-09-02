---
title: 'CA1027: Пометьте перечисления атрибутом FlagsAttribute | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 774279dd05bd14c34df7f1d450f00599812d6a5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544512"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027. Пометьте перечисляемые типы с помощью FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Значения открытого перечисления — это степени двойки или сочетания других значений, определенных в перечислении, и <xref:System.FlagsAttribute?displayProperty=fullName> атрибут отсутствует. Чтобы сократить число ложных срабатываний, это правило не сообщает о нарушении перечислений, имеющих непрерывные значения.

## <a name="rule-description"></a>Описание правила
 Перечисление является типом значения, которое определяет набор связанных именованных констант. Применяется <xref:System.FlagsAttribute> к перечислению, если его именованные константы можно комбинировать. Например, рассмотрим перечисление дней недели в приложении, которое отслеживает доступность ресурсов. Если доступность каждого ресурса кодируется с помощью имеющегося перечисления <xref:System.FlagsAttribute> , можно представить любое сочетание дней. Без атрибута можно представить только один день недели.

 Для полей, в которых хранятся комбинированные перечисления, отдельные значения перечисления обрабатываются как группы битов в поле. Поэтому такие поля иногда называют *битовыми полями*. Чтобы объединить значения перечисления для хранения в битовом поле, используйте логические условные операторы. Чтобы протестировать битовое поле для определения наличия определенного значения перечисления, используйте логические операторы логического типа. Чтобы битовое поле было правильно хранить и получать объединенные значения перечисления, каждое значение, определенное в перечислении, должно быть степенью двух. Если это не так, логические операторы логического типа не смогут извлекать отдельные значения перечисления, хранящиеся в поле.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте <xref:System.FlagsAttribute> к перечислению.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключите предупреждение из этого правила, если не нужно, чтобы значения перечисления были комбинированными.

## <a name="example"></a>Пример
 В следующем примере `DaysEnumNeedsFlags` — это перечисление, удовлетворяющее требованиям к использованию <xref:System.FlagsAttribute> , но не имеющему его. `ColorEnumShouldNotHaveFlag`Перечисление не имеет значений, которые являются степенями двух, но неправильно указывает <xref:System.FlagsAttribute> . Это нарушает правило [CA2217: не помечайте перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2217. Не помечайте перечисляемые типы с помощью FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также:
 <xref:System.FlagsAttribute?displayProperty=fullName>

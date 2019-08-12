---
title: CA1014. Пометьте сборки с помощью CLSCompliantAttribute
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f11a93380f149648ece4ae6d71bc9c2f25df5191
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923116"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014. Пометьте сборки с помощью CLSCompliantAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
К сборке не <xref:System.CLSCompliantAttribute?displayProperty=fullName> применен атрибут.

## <a name="rule-description"></a>Описание правила
Спецификация среды CLS определяет ограничения по именованию, типам данных и правилам, которым должны соответствовать сборки, предназначенные для использования в нескольких языках программирования. Хороший дизайн определяет, что все сборки явно указывают на <xref:System.CLSCompliantAttribute>соответствие CLS. Если атрибут отсутствует в сборке, сборка не соответствует требованиям.

CLS-совместимая сборка может содержать типы или члены типов, которые не соответствуют требованиям.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, добавьте атрибут в сборку. Вместо того чтобы пометить всю сборку как несоответствующую, следует определить, какие члены типа или типа не соответствуют требованиям, и пометить эти элементы как таковые. По возможности следует предоставить CLS-совместимую альтернативу для несоответствующих членов, чтобы максимально доступная аудитория могла обращаться ко всем функциональным возможностям сборки.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует. Если вы не хотите, чтобы сборка была совместимой, примените атрибут и задайте для `false`него значение.

## <a name="example"></a>Пример
В следующем примере показана сборка <xref:System.CLSCompliantAttribute?displayProperty=fullName> с примененным атрибутом, который объявляет CLS-совместимый.

[!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
[!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>См. также

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [Независимость от языка и независимые от языка компоненты](/dotnet/standard/language-independence-and-language-independent-components)
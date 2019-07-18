---
title: CA1813. Избегайте распечатанных атрибутов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0624ff6ed890b6f0c14f3a03fe774c422334737d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690295"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813. Избегайте незапечатанных атрибутов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Категория|Microsoft.Performance|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый тип наследует от <xref:System.Attribute?displayProperty=fullName>, не является абстрактным и не является запечатанным (`NotInheritable` в Visual Basic).

## <a name="rule-description"></a>Описание правила
 В библиотеке классов [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] предоставляются методы для извлечения пользовательских атрибутов. По умолчанию эти методы осуществляют поиск иерархии наследования атрибутов; например <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> производит поиск определенного типа атрибута или любой тип атрибута, который расширяет тип указанного атрибута. Запечатывание атрибута, поиск в иерархии наследования и может повысить производительность.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, запечатайте атрибут или сделать абстрактным.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила. Это следует сделать только в том случае, если при определении иерархии атрибутов и нельзя запечатать атрибут или сделать абстрактным.

## <a name="example"></a>Пример
 В примере показан настраиваемый атрибут, который соответствует данному правилу.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1019: НЕОБХОДИМО Определять методы доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: Пометьте атрибуты с помощью AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>См. также
 [Атрибуты](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)

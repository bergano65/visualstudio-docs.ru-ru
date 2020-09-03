---
title: 'CA1813: не использовать незапечатанные атрибуты | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8d86f4a9ecbdfff451fed21f93c0fe6a7679d471
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543953"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813. Избегайте незапечатанных атрибутов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Категория|Microsoft. Performance|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый тип наследует от <xref:System.Attribute?displayProperty=fullName> , не является абстрактным и не запечатан ( `NotInheritable` в Visual Basic).

## <a name="rule-description"></a>Описание правила
 В библиотеке классов [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] предоставляются методы для извлечения пользовательских атрибутов. По умолчанию эти методы выполняют поиск в иерархии наследования атрибута. Например, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> ищет указанный тип атрибута или любой тип атрибута, расширяющий указанный тип атрибута. Запечатывание атрибута позволяет исключить Поиск через иерархию наследования и повысить производительность.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, запечатайте тип атрибута или сделайте его абстрактным.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 В этом правиле можно отключить вывод предупреждений. Это следует делать только в том случае, если вы определяете иерархию атрибута и не можете запечатывать атрибут или сделать его абстрактным.

## <a name="example"></a>Пример
 В следующем примере показан настраиваемый атрибут, который удовлетворяет этому правилу.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1019. Определите методы доступа для аргументов атрибута](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018. Пометьте атрибуты с помощью AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>См. также:
 [Атрибуты](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)

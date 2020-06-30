---
title: 'CA1019: определение методов доступа для аргументов атрибутов | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ec9be9dae502ec48570a85576f483518ed0d75d6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534957"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019. Определите методы доступа для аргументов атрибута
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 В конструкторе атрибут определяет аргументы, которые не имеют соответствующих свойств.

## <a name="rule-description"></a>Описание правила
 Атрибуты могут определять обязательные аргументы, которые должны быть указаны при применении атрибута к целевому объекту. Они также известны как позиционные аргументы, поскольку предоставляются для конструкторов атрибутов в качестве позиционных параметров. Для каждого обязательного аргумента атрибут должен предоставлять соответствующее свойство, доступное только для чтения, чтобы извлечь значение аргумента во время выполнения. Это правило проверяет, что для каждого параметра конструктора определено соответствующее свойство.

 Кроме того, атрибуты могут определять дополнительные параметры, известные как именованные аргументы. Эти аргументы предоставляются для конструкторов атрибутов по имени и должны иметь соответствующее свойство чтения/записи.

 Для обязательных и необязательных аргументов соответствующие свойства и параметры конструктора должны использовать одно и то же имя, но разные регистры. В свойствах используется регистр символов Pascal, а в параметрах используется регистр Camel.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте свойство только для чтения для каждого параметра конструктора, у которого его нет.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила, если не нужно, чтобы значение обязательного аргумента было извлечено.

## <a name="custom-attributes-example"></a>Пример настраиваемых атрибутов

### <a name="description"></a>Описание
 В следующем примере показаны два атрибута, определяющих обязательный (Позиционированный) параметр. Первая реализация атрибута определена неправильно. Вторая реализация правильная.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Позиционированные и именованные аргументы

### <a name="description"></a>Описание
 Позиционированные и именованные аргументы делают ясно для потребителей библиотеки, какие аргументы являются обязательными для атрибута и какие аргументы являются необязательными.

 В следующем примере показана реализация атрибута, который содержит как позиционированные, так и именованные аргументы.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Комментарии
 В следующем примере показано, как применить пользовательский атрибут к двум свойствам.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1813. Избегайте незапечатанных атрибутов](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>См. также
 [Атрибуты](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)

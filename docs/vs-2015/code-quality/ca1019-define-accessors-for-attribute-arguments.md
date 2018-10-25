---
title: 'CA1019: необходимо Определять методы доступа для аргументов атрибута | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ff0329c5c9d565685d4e5c0ff950b31dea3299f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854893"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: необходимо определять методы доступа для аргументов атрибутов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 В своем конструкторе атрибут определяет аргументы, которые не имеют соответствующие свойства.

## <a name="rule-description"></a>Описание правила
 Атрибуты могут определять обязательные аргументы, которые должны быть указаны при применении атрибута к целевому объекту. Они также известны как позиционные аргументы, поскольку предоставляются для конструкторов атрибутов в качестве позиционных параметров. Для каждого обязательного аргумента атрибут должен предоставлять соответствующее свойство, доступное только для чтения, чтобы извлечь значение аргумента во время выполнения. Это правило проверяет, что для каждого параметра конструктора определено соответствующее свойство.

 Кроме того, атрибуты могут определять дополнительные параметры, известные как именованные аргументы. Эти аргументы предоставляются для конструкторов атрибутов по имени и должны иметь соответствующее свойство чтения/записи.

 Для обязательных и необязательных аргументов, соответствующие свойства и параметры конструктора следует использовать то же самое имя но другой регистр символов. Свойства используют Pascal, а для параметров используется смешанный регистр.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте свойство только для чтения для каждого параметра конструктора, который не имеет ни одного.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, если не хотите, чтобы значение аргумент mandatory для них.

## <a name="custom-attributes-example"></a>Пример настраиваемых атрибутов

### <a name="description"></a>Описание
 В следующем примере показано два атрибуты, определяющие обязательный параметр (позиционные). Первая реализация атрибута задано неправильно. Вторая реализация является верной.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Позиционные и именованные аргументы

### <a name="description"></a>Описание
 Позиционные и именованные аргументы упрощают для пользователей библиотеки обязательных атрибута и какие аргументы являются необязательными.

 В следующем примере показана реализация атрибута, имеющего позиционные и именованные аргументы.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Комментарии
 В следующем примере показано, как применение пользовательского атрибута к двум свойствам.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1813: избегайте распечатанных атрибутов](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>См. также
 [Атрибуты](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)




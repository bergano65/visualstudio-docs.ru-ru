---
title: 'CA1051: не объявляйте видимые поля экземпляров | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 076ce3858774d44e2d6c4c25205ced74b7a41bf0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539767"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051. Не объявляйте видимые поля экземпляров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Внешний видимый тип имеет внешнее видимое поле экземпляра.

## <a name="rule-description"></a>Описание правила
 Поля главным образом следует использовать для данных реализации. Поля должны быть `private` или `internal` и должны предоставляться с помощью свойств. Очень просто получить доступ к свойству, так как оно обращается к полю, и код в функциях доступа свойства может измениться, так как функции типа расширяются без внесения критических изменений. Свойства, которые просто возвращают значение закрытого или внутреннего поля, оптимизированы для выполнения по номиналу с доступом к полю; незначительное увеличение производительности связано с использованием внешних видимых полей, передаваемых по свойствам.

 Видимыми извне называются `public` `protected` уровни доступности,, и `protected internal` ( `Public` , `Protected` и `Protected Friend` в Visual Basic).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте поле `private` или `internal` Предоставьте его с помощью свойства, видимого извне.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Внешние видимые поля не предоставляют никаких преимуществ, недоступных для свойств. Кроме того, открытые поля не могут быть защищены [запросами компоновки](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d). См. раздел [CA2112: Secure Types не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Пример
 В следующем примере показан тип ( `BadPublicInstanceFields` ), нарушающий это правило. `GoodPublicInstanceFields`Отображает исправленный код.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2112. Защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>См. также
 [Требования связывания](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)

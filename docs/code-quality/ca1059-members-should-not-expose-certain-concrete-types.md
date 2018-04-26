---
title: 'CA1059: члены не должны предоставлять определенные устойчивые типы'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c872685445dddaf55efc8c5880b053c865ff2351
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: члены не должны предоставлять определенные устойчивые типы
|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Внешне видимый член является определенным устойчивым типом и предоставляет определенные устойчивые типы посредством одного из своих параметров или возвращаемого значения. В настоящее время это правило выдает сообщение раскрытия конкретных типов:

-   Тип, производный от <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Устойчивый тип – это тип, который имеет полную реализацию и экземпляр которого можно создать. Чтобы разрешить широкого использования этого элемента, замените конкретный тип предложенным интерфейсом. Это позволяет члену принимать любой тип, реализующий интерфейс или использоваться там, где ожидается тип, реализующий интерфейс.

 В следующей таблице перечислены целевых устойчивых типов и их предлагаемые замен.

|Устойчивый тип|Замена|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> С помощью интерфейса отделяет член от реализации источника данных XML.|

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, измените конкретный тип предложенным интерфейсом.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Безопасно предупреждения из этого правила, если конкретные функции, обеспечиваемые конкретный тип не требуется.

## <a name="related-rules"></a>Связанные правила
 [CA1011: попробуйте передать базовые типы в качестве параметров](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
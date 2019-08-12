---
title: CA1059. Члены не должны предоставлять определенные конкретные типы
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f24881d04599677c5d45c93fc940286f115d593
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922511"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059. Члены не должны предоставлять определенные конкретные типы

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Внешний видимый член является определенным конкретным типом или предоставляет определенные конкретные типы через один из его параметров или возвращаемое значение. В настоящее время это правило сообщает о раскрытии следующих конкретных типов:

- Тип, производный <xref:System.Xml.XmlNode?displayProperty=fullName>от.

## <a name="rule-description"></a>Описание правила
Устойчивый тип – это тип, который имеет полную реализацию и экземпляр которого можно создать. Чтобы обеспечить широкое использование члена, замените конкретный тип предложенным интерфейсом. Это позволяет элементу принимать любой тип, реализующий интерфейс, или использовать там, где ожидается тип, реализующий интерфейс.

В следующей таблице перечислены целевые конкретные типы и их предлагаемые замены.

|Конкретный тип|Замена|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Использование интерфейса отделяет элемент от конкретной реализации источника XML-данных.|

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, измените конкретный тип на предлагаемый интерфейс.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Можно спокойно отключить сообщение от этого правила, если требуется конкретная функциональность, предоставляемая конкретным типом.

## <a name="related-rules"></a>Связанные правила
[CA1011: Рассмотрите возможность передачи базовых типов в качестве параметров](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
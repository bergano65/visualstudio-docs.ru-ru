---
title: 'CA1059: члены не должны предоставлять определенные конкретные типы | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 792426615dd78241ade1d38a24ec1f4d5702cede
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545383"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059. Члены не должны предоставлять определенные конкретные типы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Внешний видимый член является определенным конкретным типом или предоставляет определенные конкретные типы через один из его параметров или возвращаемое значение. В настоящее время это правило сообщает о раскрытии следующих конкретных типов:

- Тип, производный от <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Устойчивый тип – это тип, который имеет полную реализацию и экземпляр которого можно создать. Чтобы обеспечить широкое использование члена, замените конкретный тип предложенным интерфейсом. Это позволяет элементу принимать любой тип, реализующий интерфейс, или использовать там, где ожидается тип, реализующий интерфейс.

 В следующей таблице перечислены целевые конкретные типы и их предлагаемые замены.

|Конкретный тип|Замена|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Использование интерфейса отделяет элемент от конкретной реализации источника XML-данных.|

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените конкретный тип на предлагаемый интерфейс.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно спокойно отключить сообщение от этого правила, если требуется конкретная функциональность, предоставляемая конкретным типом.

## <a name="related-rules"></a>Связанные правила
 [CA1011. Попробуйте передать базовые типы в качестве параметров](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)

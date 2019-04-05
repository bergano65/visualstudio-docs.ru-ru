---
title: CA1059. Члены не должны предоставлять определенные устойчивые типы | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 46e3941e1aab0e2f6f532a7a394437a0613b8d8d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990120"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059. Члены не должны предоставлять определенные конкретные типы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Внешне видимый член является определенным устойчивым типом или предоставляет определенные устойчивые типы посредством одного из своих параметров или возвращаемого значения. В настоящее время это правило выдает сообщение раскрытия следующие конкретные типы:

-   Тип, производный от <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Устойчивый тип – это тип, который имеет полную реализацию и экземпляр которого можно создать. Чтобы разрешить широкого использования этого элемента, замените конкретный тип предложенным интерфейсом. Это позволяет члену принимать любой тип, реализующий интерфейс или использоваться там, где ожидается тип, реализующий интерфейс.

 Ниже перечислены целевых устойчивых типов и их предлагаемые замен.

|Конкретный тип|Замена|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> С помощью интерфейса отделяет член от реализации источника данных XML.|

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените конкретный тип предложенным интерфейсом.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить сообщение из этого правила, если конкретные функции, обеспечиваемые конкретный тип является обязательным.

## <a name="related-rules"></a>Связанные правила
 [CA1011: Попробуйте передать базовые типы в качестве параметров](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)

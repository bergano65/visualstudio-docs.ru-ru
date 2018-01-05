---
title: "CA1059: Члены не должны предоставлять определенные устойчивые типы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eae9070d76312fa4840f2cf8724a74a2cde4f7b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
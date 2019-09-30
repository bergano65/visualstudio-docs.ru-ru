---
title: CA2212. Не помечайте обслуживаемые компоненты с помощью WebMethod
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b2ace5f6e51fc7a8d29faab14cc2332fd808f93
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231653"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212. Не помечайте обслуживаемые компоненты с помощью WebMethod

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Категория|Microsoft. Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Метод в типе, который наследуется от <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> , <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>помечается атрибутом.

## <a name="rule-description"></a>Описание правила

<xref:System.Web.Services.WebMethodAttribute>применяется к методам в веб-службе XML, созданным с помощью ASP.NET; Он делает метод вызываемым из удаленных веб-клиентов. Метод и класс должны быть общедоступными и выполняться в веб-приложении ASP.NET. <xref:System.EnterpriseServices.ServicedComponent>типы размещаются в приложениях COM+ и могут использовать службы COM+. <xref:System.Web.Services.WebMethodAttribute>не применяется к <xref:System.EnterpriseServices.ServicedComponent> типам, так как они не предназначены для одних и тех же сценариев. В частности, добавление атрибута в <xref:System.EnterpriseServices.ServicedComponent> метод не делает метод вызываемым из удаленных веб-клиентов. <xref:System.Web.Services.WebMethodAttribute> Поскольку<xref:System.EnterpriseServices.ServicedComponent> и метод имеют конфликтующие поведения и требования для контекста и потока транзакций, поведение метода в некоторых сценариях будет неправильным.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите атрибут из <xref:System.EnterpriseServices.ServicedComponent> метода.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует. Нет сценариев, в которых сочетание этих элементов является правильным.

## <a name="see-also"></a>См. также

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
---
title: 'CA2212: не следует помечать обслуживаемые компоненты атрибутом WebMethod'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ee4371f44a8a8c2acd0b20f48fcc89a1242b4df
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: не следует помечать обслуживаемые компоненты атрибутом WebMethod
|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Категория|Microsoft.Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод в типе, который наследует от <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> помечается <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 <xref:System.Web.Services.WebMethodAttribute> применяется к методам в пределах веб-служб XML, созданных с помощью ASP.NET; он позволяет вызывать метод из удаленного веб-клиентов. Метод и класс должен быть открытыми и выполняться в веб-приложения ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> типы поддерживаемых приложений COM + и могут использовать службы COM +. <xref:System.Web.Services.WebMethodAttribute> не применяется к <xref:System.EnterpriseServices.ServicedComponent> типы, поскольку они не предназначены для сценариев. В частности, добавление атрибута к <xref:System.EnterpriseServices.ServicedComponent> метод не выполняет метод вызываемой удаленных веб-клиентов. Поскольку <xref:System.Web.Services.WebMethodAttribute> и <xref:System.EnterpriseServices.ServicedComponent> метод иметь конфликтующие поведения и требования для контекста и потока транзакций, поведение метода будет неправильным в некоторых сценариях.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, удалите атрибут из <xref:System.EnterpriseServices.ServicedComponent> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Не существует сценариев которых сочетание этих элементов допустимо.

## <a name="see-also"></a>См. также
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
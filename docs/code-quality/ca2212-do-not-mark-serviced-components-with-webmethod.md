---
title: 'CA2212: не следует помечать обслуживаемые компоненты атрибутом WebMethod'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 88708fdcb41a43d3e8b3f78b4e66decb7211a4b4
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177426"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: не следует помечать обслуживаемые компоненты атрибутом WebMethod

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Категория|Microsoft.Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Метод в тип, наследующий от <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> помечается <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила

<xref:System.Web.Services.WebMethodAttribute> применяется к методам веб-службы XML, которые были созданы с помощью ASP.NET; Она позволяет вызывать метод из удаленного веб-клиентов. Метод и класс должен быть открытыми и выполняться в веб-приложения ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> типы, которые размещаются приложения COM + и могут использовать службы COM +. <xref:System.Web.Services.WebMethodAttribute> не применяется к <xref:System.EnterpriseServices.ServicedComponent> типов, так как они не предназначены для сценариев. В частности, добавление атрибута к <xref:System.EnterpriseServices.ServicedComponent> метод не выполняет метод вызываемой от удаленного веб-клиентов. Так как <xref:System.Web.Services.WebMethodAttribute> и <xref:System.EnterpriseServices.ServicedComponent> метод имеют конфликтующие поведения и требования для контекста и потока транзакций, поведение метода будет неправильным в некоторых сценариях.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите атрибут из <xref:System.EnterpriseServices.ServicedComponent> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует. Не существует сценариев которых допустимо сочетание этих элементов.

## <a name="see-also"></a>См. также

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
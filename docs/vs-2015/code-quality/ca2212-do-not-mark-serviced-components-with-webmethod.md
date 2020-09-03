---
title: 'CA2212: не помечать обслуживаемые компоненты с помощью WebMethod | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3c707fef5562b932b6232300131f6e6e6efef6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534567"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212. Не помечайте обслуживаемые компоненты с помощью WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Категория|Microsoft. Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод в типе, который наследуется от <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> , помечается атрибутом <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> .

## <a name="rule-description"></a>Описание правила
 <xref:System.Web.Services.WebMethodAttribute> применяется к методам в веб-службе XML, созданным с помощью ASP.NET; Он делает метод вызываемым из удаленных веб-клиентов. Метод и класс должны быть общедоступными и выполняться в веб-приложении ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> типы размещаются в приложениях COM+ и могут использовать службы COM+. <xref:System.Web.Services.WebMethodAttribute> не применяется к <xref:System.EnterpriseServices.ServicedComponent> типам, так как они не предназначены для одних и тех же сценариев. В частности, добавление атрибута в <xref:System.EnterpriseServices.ServicedComponent> метод не делает метод вызываемым из удаленных веб-клиентов. Поскольку <xref:System.Web.Services.WebMethodAttribute> и <xref:System.EnterpriseServices.ServicedComponent> метод имеют конфликтующие поведения и требования для контекста и потока транзакций, поведение метода в некоторых сценариях будет неправильным.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите атрибут из <xref:System.EnterpriseServices.ServicedComponent> метода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Нет сценариев, в которых сочетание этих элементов является правильным.

## <a name="see-also"></a>См. также:
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>

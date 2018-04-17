---
title: 'CA2212: Не следует помечать обслуживаемые компоненты атрибутом WebMethod | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: ca33b1dfeafa3894b3ad82fd42a04d8310d2bd50
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
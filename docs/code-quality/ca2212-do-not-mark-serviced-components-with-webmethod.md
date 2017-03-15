---
title: "CA2212: не следует помечать обслуживаемые компоненты атрибутом WebMethod | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
helpviewer_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2212: не следует помечать обслуживаемые компоненты атрибутом WebMethod
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotMarkServicedComponentsWithWebMethod|  
|CheckId|CA2212|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Метод в типе, наследуемом от <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>, помечен атрибутом <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.  
  
## Описание правила  
 <xref:System.Web.Services.WebMethodAttribute> применяется к методам в веб\-службе XML, которая была создана с помощью ASP.NET; этот атрибут обеспечивает возможность вызова данного метода удаленными веб\-клиентами.  Такой метод и класс должны быть открытыми и выполняться внутри веб\-приложения ASP.NET.  Типы <xref:System.EnterpriseServices.ServicedComponent> размещаются приложениями COM\+ и могут использовать службы COM\+.  <xref:System.Web.Services.WebMethodAttribute> не применяется к типам <xref:System.EnterpriseServices.ServicedComponent>, поскольку они не предназначены для того же сценария.  В частности, при добавлении атрибута к методу <xref:System.EnterpriseServices.ServicedComponent> этот метод не становится доступным для вызова удаленными веб\-клиентами.  <xref:System.Web.Services.WebMethodAttribute> и метод <xref:System.EnterpriseServices.ServicedComponent> ведут себя по\-разному и имеют разные требования к контексту и потоку транзакций, поэтому поведение метода будет неверным в некоторых скриптах.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, удалите атрибут из метода <xref:System.EnterpriseServices.ServicedComponent>.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Не существует скриптов, в которых сочетание этих элементов допустимо.  
  
## См. также  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
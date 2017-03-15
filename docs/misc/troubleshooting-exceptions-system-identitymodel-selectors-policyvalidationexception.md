---
title: "Разрешение вопросов, связанных с исключениями: System.IdentityModel.Selectors.PolicyValidationException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PolicyValidationException - исключение"
  - "System.IdentityModel.Selectors.PolicyValidationException - исключение"
ms.assetid: 510c7698-a12b-4bcb-a9d8-87c704b62ffa
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.IdentityModel.Selectors.PolicyValidationException
Исключение <xref:System.IdentityModel.Selectors.PolicyValidationException> вызывается при неудачной проверке политики, предоставляемой адресатом. Дополнительные сведения о требованиях политики см. в разделе [Технический справочник по Information Card Profile V1.0](http://go.microsoft.com/fwlink/?LinkID=102401).  
  
 Любое недопустимое содержимое политики может вызвать этот сбой. К наиболее частым проблемам политики относятся:  
  
-   Недопустимый тип ключа  
  
-   Недопустимый размер ключа  
  
-   Недопустимый XML  
  
-   В политике не указано ни одного требования \(по крайней мере одно из обязательных требований должно быть указано\).  
  
## См. также  
 <xref:System.IdentityModel.Selectors.PolicyValidationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)
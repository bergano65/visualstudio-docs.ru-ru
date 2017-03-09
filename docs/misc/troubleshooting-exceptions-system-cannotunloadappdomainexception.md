---
title: "Разрешение вопросов, связанных с исключениями: System.CannotUnloadAppDomainException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "CannotUnloadAppDomainException - класс"
ms.assetid: eeee07c3-fdbc-4c91-859b-a419d23be9ba
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.CannotUnloadAppDomainException
Исключение <xref:System.CannotUnloadAppDomainException> вызывается при попытке выгрузить:  
  
-   Домен приложения по умолчанию, который должен оставаться загруженным во время всей жизни приложения.  
  
-   Домен приложения с запущенным потоком, который не может немедленно прекратить выполнение.  
  
-   Уже выгруженный домен приложения.  
  
## Полезные советы  
 **Убедитесь, что не предпринималась попытка выгрузить домен приложения, используемый по умолчанию, домен, который имеет выполняющийся поток, или домен, который уже был выгружен.**  
 Любое из этих условий приведёт к созданию исключения. Для получения дополнительной информации см. <xref:System.AppDomain.Unload%2A>.  
  
## См. также  
 <xref:System.CannotUnloadAppDomainException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)
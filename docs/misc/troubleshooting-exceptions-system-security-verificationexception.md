---
title: "Разрешение вопросов, связанных с исключениями: System.Security.VerificationException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHVerification"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "VerificationException - класс"
ms.assetid: b7b1a4c2-6769-46bd-8912-ebbfe226bfb3
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Security.VerificationException
Исключение <xref:System.Security.VerificationException> генерируется, если в политику безопасности входит требование типобезопасности кода, а в ходе проверки невозможно определить, выполнено ли оно в коде.  
  
## Полезные советы  
 Убедитесь, что приложение не загружает две конфликтующие версии библиотеки классов.  
 В процессе проверки код MSIL проверяется на строгую типизацию для того, чтобы объекты были безопасно изолированы друг от друга и, соответственно, ограждены от случайного или злонамеренного повреждения. Для получения дополнительной информации см. [Строгая типизация и безопасность](http://msdn.microsoft.com/ru-ru/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc).  
  
## См. также  
 <xref:System.Security.VerificationException>   
 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)
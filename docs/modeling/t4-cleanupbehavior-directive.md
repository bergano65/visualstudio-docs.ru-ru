---
title: "Директива T4 CleanUpBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Директива T4 CleanUpBehavior
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Для удаления appDomain после обработки текстового шаблона добавьте следующую строку:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Текстовые шаблоны обрабатываются в appDomain, который отличается от хост\-процесса.  В большинстве случаев после обработки одного текстового шаблона appDomain снова используется для обработки следующего шаблона.  Но если указан атрибут CleanupBehavior, appDomain удаляется и следующий шаблон обрабатывается в новом appDomain.  
  
 Это замедляет обработку текста, но может быть полезно для гарантированного удаления ресурсов.  
  
 Эта директива работает только в узле Visual Studio.
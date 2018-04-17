---
title: Директива T4 CleanUpBehavior | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: d0a03a57734a6536c147759ea05745497eeeffa1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="t4-cleanupbehavior-directive"></a>Директива T4 CleanUpBehavior
Для удаления appDomain после обработки текстового шаблона добавьте следующую строку:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Текстовые шаблоны обрабатываются в appDomain, который отличается от хост-процесса. В большинстве случаев после обработки одного текстового шаблона appDomain снова используется для обработки следующего шаблона. Но если указан атрибут CleanupBehavior, appDomain удаляется и следующий шаблон обрабатывается в новом appDomain.  
  
 Это замедляет обработку текста, но может быть полезно для гарантированного удаления ресурсов.  
  
 Эта директива работает только в узле Visual Studio.
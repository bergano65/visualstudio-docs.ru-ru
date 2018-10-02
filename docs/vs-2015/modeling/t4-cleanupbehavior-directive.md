---
title: Директива T4 CleanUpBehavior | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9b9138ab564c7597715537216333f1efd0f3fc5a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563911"
---
# <a name="t4-cleanupbehavior-directive"></a>Директива T4 CleanUpBehavior
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [директива T4 CleanUpBehavior](https://docs.microsoft.com/visualstudio/modeling/t4-cleanupbehavior-directive).  
  
Для удаления appDomain после обработки текстового шаблона добавьте следующую строку:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Текстовые шаблоны обрабатываются в appDomain, который отличается от хост-процесса. В большинстве случаев после обработки одного текстового шаблона appDomain снова используется для обработки следующего шаблона. Но если указан атрибут CleanupBehavior, appDomain удаляется и следующий шаблон обрабатывается в новом appDomain.  
  
 Это замедляет обработку текста, но может быть полезно для гарантированного удаления ресурсов.  
  
 Эта директива работает только в узле Visual Studio.




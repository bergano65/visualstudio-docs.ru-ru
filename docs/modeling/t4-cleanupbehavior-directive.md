---
title: Директива T4 CleanUpBehavior
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: f99cece37b37cdbf4906e9af3939fe824aec0a93
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912825"
---
# <a name="t4-cleanupbehavior-directive"></a>Директива T4 CleanUpBehavior

Для удаления appDomain после обработки текстового шаблона добавьте следующую строку:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Текстовые шаблоны обрабатываются в appDomain, который отличается от хост-процесса. В большинстве случаев после обработки одного текстового шаблона appDomain снова используется для обработки следующего шаблона. Но если указан атрибут CleanupBehavior, appDomain удаляется и следующий шаблон обрабатывается в новом appDomain.

Это замедляет обработку текста, но может быть полезно для гарантированного удаления ресурсов.

Эта директива работает только в узле Visual Studio.
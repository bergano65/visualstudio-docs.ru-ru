---
title: Директива T4 CleanUpBehavior
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da296be872daa89d2759566020452fab4951d3b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606488"
---
# <a name="t4-cleanupbehavior-directive"></a>Директива T4 CleanUpBehavior

Для удаления appDomain после обработки текстового шаблона добавьте следующую строку:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Текстовые шаблоны обрабатываются в appDomain, который отличается от хост-процесса. В большинстве случаев после обработки одного текстового шаблона appDomain снова используется для обработки следующего шаблона. Но если указан атрибут CleanupBehavior, appDomain удаляется и следующий шаблон обрабатывается в новом appDomain.

Это замедляет обработку текста, но может быть полезно для гарантированного удаления ресурсов.

Эта директива работает только в узле Visual Studio.
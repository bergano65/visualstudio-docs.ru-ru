---
title: Директива T4 CleanUpBehavior
description: Сведения об директиве Клеанупбехавиор и об удалении appDomain после обработки текстового шаблона.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c07d0bf714d42cc605d76d593ed48a70b925483
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363683"
---
# <a name="t4-cleanupbehavior-directive"></a>Директива T4 CleanUpBehavior

Для удаления appDomain после обработки текстового шаблона добавьте следующую строку:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Текстовые шаблоны обрабатываются в appDomain, который отличается от хост-процесса. В большинстве случаев после обработки одного текстового шаблона appDomain снова используется для обработки следующего шаблона. Но если указан атрибут CleanupBehavior, appDomain удаляется и следующий шаблон обрабатывается в новом appDomain.

Это замедляет обработку текста, но может быть полезно для гарантированного удаления ресурсов.

Эта директива работает только в узле Visual Studio.

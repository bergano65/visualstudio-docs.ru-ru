---
title: Директива T4 CleanUpBehavior
description: Сведения об директиве Клеанупбехавиор и об удалении appDomain после обработки текстового шаблона.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 49609dd13e2e322f88f265d27e55c49154f4c5c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899657"
---
# <a name="t4-cleanupbehavior-directive"></a>Директива T4 CleanUpBehavior

Для удаления appDomain после обработки текстового шаблона добавьте следующую строку:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Текстовые шаблоны обрабатываются в appDomain, который отличается от хост-процесса. В большинстве случаев после обработки одного текстового шаблона appDomain снова используется для обработки следующего шаблона. Но если указан атрибут CleanupBehavior, appDomain удаляется и следующий шаблон обрабатывается в новом appDomain.

Это замедляет обработку текста, но может быть полезно для гарантированного удаления ресурсов.

Эта директива работает только в узле Visual Studio.

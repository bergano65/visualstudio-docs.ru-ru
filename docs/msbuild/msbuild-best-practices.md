---
title: Рекомендации по MSBuild | Документация Майкрософт
description: Рекомендации по написанию скриптов MSBuild. Например, следует использовать атрибуты Condition и не следует применять подстановочные знаки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2742324f737a4e70221e3cbe4c78cff56fa7e7ca
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047665"
---
# <a name="msbuild-best-practices"></a>Рекомендации по MSBuild

При создании скриптов MSBuild рекомендуется следовать следующим правилам.

- Для более эффективной обработки значений свойств по умолчанию рекомендуется использовать атрибут `Condition`, а не объявлять свойство, значение по умолчанию которого можно переопределить в командной строке. Например, используйте

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Как правило, при выборе элементов не следует использовать подстановочные знаки. Файлы необходимо указывать явным образом. Это связано с тем, что в большинстве типов проектов MSBuild развертывает подстановочные знаки в разное время, например, при добавлении или удалении элементов, что может привести к непредвиденному поведению. Исключением из этого являются проекты в стиле пакета SDK для .NET Core, которые правильно обрабатывают подстановочные знаки.

## <a name="see-also"></a>См. также

- [Дополнительные возможности](../msbuild/msbuild-advanced-concepts.md)

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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 83527ac4b7d16d2cb06c797924c18f2567f12350
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919183"
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

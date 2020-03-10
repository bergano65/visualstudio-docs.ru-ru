---
title: Рекомендации по MSBuild | Документация Майкрософт
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
ms.openlocfilehash: 91b2e157ee64f5e4d91bc75a5d6f8d65d4312862
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263153"
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

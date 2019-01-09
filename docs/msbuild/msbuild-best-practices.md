---
title: Рекомендации по MSBuild | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8140a8f2bfa4c80f0f56e3271e17371ccf0ec95c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858271"
---
# <a name="msbuild-best-practices"></a>Рекомендации по MSBuild
При создании скриптов MSBuild рекомендуется следовать следующим правилам.  
  
-   Для более эффективной обработки значений свойств по умолчанию рекомендуется использовать атрибут `Condition`, а не объявлять свойство, значение по умолчанию которого можно переопределить в командной строке. Например, используйте  
  
```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```
  
-   При выборе элементов избегайте подстановочных знаков. Файлы необходимо указывать явным образом. Это упрощает процесс отслеживания ошибок, которые могут возникнуть при добавлении или удалении файлов.  
  
## <a name="see-also"></a>См. также  
 [Дополнительные возможности](../msbuild/msbuild-advanced-concepts.md)

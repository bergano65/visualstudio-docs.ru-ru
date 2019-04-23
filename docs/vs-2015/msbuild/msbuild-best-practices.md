---
title: Рекомендации по MSBuild | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e597b10913ad495193545ab304b3b324d8f66b41
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043425"
---
# <a name="msbuild-best-practices"></a>Рекомендации по MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При создании скриптов MSBuild рекомендуется следовать следующим правилам.  
  
- Для более эффективной обработки значений свойств по умолчанию рекомендуется использовать атрибут `Condition`, а не объявлять свойство, значение по умолчанию которого можно переопределить в командной строке. Например, используйте  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
- При выборе элементов избегайте подстановочных знаков. Файлы необходимо указывать явным образом. Это упрощает процесс отслеживания ошибок, которые могут возникнуть при добавлении или удалении файлов.  
  
## <a name="see-also"></a>См. также раздел  
 [Дополнительные возможности](../msbuild/msbuild-advanced-concepts.md)

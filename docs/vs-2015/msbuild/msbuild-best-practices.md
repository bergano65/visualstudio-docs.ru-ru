---
title: Рекомендации по MSBuild | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df388b4b5aeac30e5ee83e24dc08905507318f18
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562086"
---
# <a name="msbuild-best-practices"></a>Рекомендации по MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [рекомендации по MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-best-practices).  
  
  
При создании скриптов MSBuild рекомендуется следовать следующим правилам.  
  
-   Для более эффективной обработки значений свойств по умолчанию рекомендуется использовать атрибут `Condition`, а не объявлять свойство, значение по умолчанию которого можно переопределить в командной строке. Например, используйте  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   При выборе элементов избегайте подстановочных знаков. Файлы необходимо указывать явным образом. Это упрощает процесс отслеживания ошибок, которые могут возникнуть при добавлении или удалении файлов.  
  
## <a name="see-also"></a>См. также  
 [Дополнительные возможности](../msbuild/msbuild-advanced-concepts.md)




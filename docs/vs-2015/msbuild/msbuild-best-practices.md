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
ms.openlocfilehash: 6973e905a0587ffdc7cbd0a401e03f933fc60a3a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662223"
---
# <a name="msbuild-best-practices"></a>Рекомендации по MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При создании скриптов MSBuild рекомендуется следовать следующим правилам.  
  
-   Для более эффективной обработки значений свойств по умолчанию рекомендуется использовать атрибут `Condition`, а не объявлять свойство, значение по умолчанию которого можно переопределить в командной строке. Например, используйте  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   При выборе элементов избегайте подстановочных знаков. Файлы необходимо указывать явным образом. Это упрощает процесс отслеживания ошибок, которые могут возникнуть при добавлении или удалении файлов.  
  
## <a name="see-also"></a>См. также раздел  
 [Дополнительные возможности](../msbuild/msbuild-advanced-concepts.md)

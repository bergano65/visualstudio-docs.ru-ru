---
title: Специальные знаки MSBuild | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a54f446cb82b3181ee057d4887b37940868a5920
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150768"
---
# <a name="msbuild-special-characters"></a>Специальные символы в MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] резервирует некоторые знаки для специального применения в определенных контекстах. Эти знаки следует экранировать, только если вы хотите использовать их именно в том контексте, для которого они зарезервированы. Например, звездочка имеет специальное значение только в атрибутах `Include` и `Exclude` определения элемента, а также в вызовах `CreateItem`. Если требуется, чтобы звездочка отображалась как звездочка в одном из этих контекстов, нужно экранировать ее. В любом другом контексте просто введите звездочку там, где она нужна.  
  
 Чтобы экранировать специальный знак, используйте синтаксис %*xx*, где *xx* представляет шестнадцатеричное ASCII-значение знака. Дополнительные сведения см. в разделе [Практическое руководство. Пропуск специальных знаков в MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Специальные символы  
 В следующей таблице перечислены специальные знаки [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]:  
  
|**Знак**|**ASCII**|**Зарезервированное использование**|  
|-------------------|---------------|------------------------|  
|%|%25|Ссылки на метаданные|  
|$|%24|Ссылки на свойства|  
|@|%40|Списки элементов|  
|'|%27|Условия и другие выражения|  
|;|%3B|Разделитель элементов списка|  
|?|%3F|Подстановочный знак для имен файлов в атрибутах `Include` и `Exclude`|  
|*|%2A|Подстановочный знак для использования в именах файлов в атрибутах `Include` и `Exclude`|  
  
## <a name="see-also"></a>См. также  
 [Дополнительные возможности](../msbuild/msbuild-advanced-concepts.md)   
 [Элементы](../msbuild/msbuild-items.md)

---
title: Специальные знаки MSBuild | Документы Майкрософт
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
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fcbafb43a059221e5572c9c807cadfdefe68134
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563282"
---
# <a name="msbuild-special-characters"></a>Специальные символы в MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [специальные символы MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-special-characters).  
  
  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] резервирует некоторые знаки для специального применения в определенных контекстах. Эти знаки следует экранировать, только если вы хотите использовать их именно в том контексте, для которого они зарезервированы. Например, звездочка имеет специальное значение только в атрибутах `Include` и `Exclude` определения элемента, а также в вызовах `CreateItem`. Если требуется, чтобы звездочка отображалась как звездочка в одном из этих контекстов, нужно экранировать ее. В любом другом контексте просто введите звездочку там, где она нужна.  
  
 Чтобы экранировать специальный знак, используйте синтаксис %*xx*, где *xx* представляет шестнадцатеричное ASCII-значение знака. Дополнительные сведения см. в статье [How to: Escape Special Characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md) (Как обеспечить пропуск специальных знаков в MSBuild).  
  
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




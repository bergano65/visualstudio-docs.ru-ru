---
title: "Специальные знаки MSBuild | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e1d7dc27d4a831e8e0a54cada37fcfdb94afd718
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-special-characters"></a>Специальные символы в MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] резервирует некоторые знаки для специального применения в определенных контекстах. Эти знаки следует экранировать, только если вы хотите использовать их именно в том контексте, для которого они зарезервированы. Например, звездочка имеет специальное значение только в атрибутах `Include` и `Exclude` определения элемента, а также в вызовах `CreateItem`. Если требуется, чтобы звездочка отображалась как звездочка в одном из этих контекстов, нужно экранировать ее. В любом другом контексте просто введите звездочку там, где она нужна.  
  
 Чтобы экранировать специальный знак, используйте синтаксис %*xx*, где *xx* представляет шестнадцатеричное ASCII-значение знака. Дополнительные сведения см. в статье [How to: Escape Special Characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md) (Как обеспечить пропуск специальных знаков в MSBuild).  
  
## <a name="special-characters"></a>Специальные символы  
 В следующей таблице перечислены специальные знаки [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]:  
  
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
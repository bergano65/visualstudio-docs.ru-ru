---
title: Как выполнить Выбор цели для первой сборки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e1ba67ee5a4ea6831d21163b467f5d638a6f16c5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967035"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Как выполнить Выбор цели для первой сборки
Файл проекта может содержать один или несколько элементов `Target`, определяющих способ сборки проекта. Модуль [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) выполняет сборку первого найденного проекта, а также всех зависимостей, если только файл проекта не содержит атрибут `DefaultTargets` или `InitialTargets` либо целевой объект не указан в командной строке с помощью параметра **-target**.  
  
## <a name="use-the-initialtargets-attribute"></a>Использование атрибута InitialTargets  
 Атрибут `InitialTargets` элемента `Project` указывает целевой объект, который будет выполняться первым, даже если целевые объекты указаны в командной строке или в атрибуте `DefaultTargets`.  
  
#### <a name="to-specify-one-initial-target"></a>Задание одного начального целевого объекта  
  
- Укажите целевой объект по умолчанию в атрибуте `InitialTargets` элемента `Project`. Например:  
  
   `<Project InitialTargets="Clean">`  
  
  В атрибуте `InitialTargets` можно указать сразу несколько начальных целевых объектов, расположив их по порядку и разделив точкой с запятой. Целевые объекты в этом списке будут выполняться последовательно.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Задание нескольких начальных целевых объектов  
  
-   Укажите начальные целевые объекты, разделенные точкой с запятой, в атрибуте `InitialTargets` элемента `Project`. Например, чтобы выполнить целевой объект `Clean` и затем `Compile`, введите:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="use-the-defaulttargets-attribute"></a>Использование атрибута DefaultTargets  
 Атрибут `DefaultTargets` элемента `Project` указывает, какой целевой объект или целевые объекты создаются, если целевой объект не задан явным образом в командной строке. Если целевые объекты указаны в обоих атрибутах `InitialTargets` и `DefaultTargets` и не указаны в командной строке, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] выполняет целевые объекты, указанные в атрибуте `InitialTargets`, а затем целевые объекты, указанные в атрибуте `DefaultTargets`.  
  
#### <a name="to-specify-one-default-target"></a>Задание одного целевого объекта по умолчанию  
  
- Укажите целевой объект по умолчанию в атрибуте `DefaultTargets` элемента `Project`. Например:  
  
   `<Project DefaultTargets="Compile">`  
  
  В атрибуте `DefaultTargets` можно указать сразу несколько целевых объектов по умолчанию, расположив их по порядку и разделив точкой с запятой. Целевые объекты в этом списке будут выполняться последовательно.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Задание нескольких целевых объектов по умолчанию  
  
-   Укажите целевые объекты по умолчанию, разделенные точкой с запятой, в атрибуте `DefaultTargets` элемента `Project`. Например, чтобы выполнить целевой объект `Clean` и затем `Compile`, введите:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="use-the--target-switch"></a>Использование параметра -target  
 Если целевой объект по умолчанию не определен в файле проекта или вы не хотите использовать его, можно использовать параметр командной строки **-target**, чтобы указать другой целевой объект. Целевые объекты, заданные с помощью параметра **-target**, выполняются вместо целевых объектов, заданных в атрибуте `DefaultTargets`. Целевые объекты, заданные в атрибуте `InitialTargets`, всегда выполняются первыми.  
 
 
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Использование целевого объекта, отличного от заданного по умолчанию, в первую очередь  
  
-   Укажите целевой объект в качестве первого с помощью параметра командной строки **-target**. Например:  
  
     `msbuild file.proj -target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Использование нескольких целевых объектов, отличных от заданных по умолчанию, в первую очередь  
  
-   Задайте целевые объекты, разделяя их точками с запятой или запятыми, с помощью параметра командной строки **-target**. Например:  
  
     `msbuild <file name>.proj -t:Clean;Compile`  
  
## <a name="see-also"></a>См. также
  [MSBuild](../msbuild/msbuild.md)  
 [Целевые объекты](../msbuild/msbuild-targets.md)   
 [Практическое руководство. Очистка сборки](../msbuild/how-to-clean-a-build.md)

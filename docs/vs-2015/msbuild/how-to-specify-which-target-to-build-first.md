---
title: Практическое руководство. Выбор цели для первой сборки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d7d47746aed2e663eb1fa25e3bb9ca2c6bed2c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178336"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Практическое руководство. Выбор цели для первого построения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Файл проекта может содержать один или несколько элементов `Target`, определяющих способ сборки проекта. [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)]Ядро ( [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ) выполняет сборку первого найденного проекта, а все зависимости, если файл проекта не содержит `DefaultTargets` атрибут, `InitialTargets` атрибут или целевой объект, указаны в командной строке с параметром **/Target** .  
  
## <a name="using-the-initialtargets-attribute"></a>Использование атрибута InitialTargets  
 Атрибут `InitialTargets` элемента `Project` указывает целевой объект, который будет выполняться первым, даже если целевые объекты указаны в командной строке или в атрибуте `DefaultTargets`.  
  
#### <a name="to-specify-one-initial-target"></a>Задание одного начального целевого объекта  
  
- Укажите целевой объект по умолчанию в атрибуте `InitialTargets` элемента `Project`. Пример:  
  
   `<Project InitialTargets="Clean">`  
  
  В атрибуте `InitialTargets` можно указать сразу несколько начальных целевых объектов, расположив их по порядку и разделив точкой с запятой. Целевые объекты в этом списке будут выполняться последовательно.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Задание нескольких начальных целевых объектов  
  
- Укажите начальные целевые объекты, разделенные точкой с запятой, в атрибуте `InitialTargets` элемента `Project`. Например, чтобы выполнить целевой объект `Clean` и затем `Compile`, введите:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>Использование атрибута DefaultTargets  
 Атрибут `DefaultTargets` элемента `Project` указывает, какой целевой объект или целевые объекты создаются, если целевой объект не задан явным образом в командной строке. Если целевые объекты указаны в обоих атрибутах `InitialTargets` и `DefaultTargets` и не указаны в командной строке, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] выполняет целевые объекты, указанные в атрибуте `InitialTargets`, а затем целевые объекты, указанные в атрибуте `DefaultTargets`.  
  
#### <a name="to-specify-one-default-target"></a>Задание одного целевого объекта по умолчанию  
  
- Укажите целевой объект по умолчанию в атрибуте `DefaultTargets` элемента `Project`. Пример:  
  
   `<Project DefaultTargets="Compile">`  
  
  В атрибуте `DefaultTargets` можно указать сразу несколько целевых объектов по умолчанию, расположив их по порядку и разделив точкой с запятой. Целевые объекты в этом списке будут выполняться последовательно.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Задание нескольких целевых объектов по умолчанию  
  
- Укажите целевые объекты по умолчанию, разделенные точкой с запятой, в атрибуте `DefaultTargets` элемента `Project`. Например, чтобы выполнить целевой объект `Clean` и затем `Compile`, введите:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>Использование параметра /target  
 Если целевой объект по умолчанию не определен в файле проекта или если вы не хотите использовать этот целевой объект по умолчанию, можно использовать параметр командной строки **/Target** , чтобы указать другой целевой объект. Целевой объект или целевые объекты, указанные с параметром **/Target** , выполняются вместо целевых объектов, заданных `DefaultTargets` атрибутом. Целевые объекты, заданные в атрибуте `InitialTargets`, всегда выполняются первыми.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Использование целевого объекта, отличного от заданного по умолчанию, в первую очередь  
  
- Укажите целевой объект в качестве первого целевого объекта с помощью параметра командной строки **/Target** . Пример:  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Использование нескольких целевых объектов, отличных от заданных по умолчанию, в первую очередь  
  
- Перечислите целевые объекты, разделяя их точкой с запятой или запятыми, с помощью параметра командной строки **/Target** . Пример:  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>См. также:
  [MSBuild](msbuild.md)  
 [Цели](../msbuild/msbuild-targets.md)   
 [Как очистить сборку](../msbuild/how-to-clean-a-build.md)

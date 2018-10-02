---
title: Метаданные элементов в пакетной обработке целевых объектов | Документы Майкрософт
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
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2d91e294165012bea3b1ac196011cf9908469a7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558860"
---
# <a name="item-metadata-in-target-batching"></a>Метаданные элементов в пакетной обработке целевых объектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [метаданные элементов в пакетной обработке целевых объектов](https://docs.microsoft.com/visualstudio/msbuild/item-metadata-in-target-batching).  
  
  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] может анализировать зависимости для входных и выходных данных целевого объекта сборки. Если определено, что входные или выходные данные целевого объекта актуальны, он пропускается, а сборка продолжается. Элементы `Target` используют атрибуты `Inputs` и `Outputs`, чтобы задать элементы, обрабатываемые во время анализа зависимостей.  
  
 Если целевой объект содержит задачу, которая использует пакетные элементы в качестве входных и выходных данных, элемент `Target` целевого объекта должен использовать пакетную обработку в своих атрибутах `Inputs` или `Outputs`, чтобы позволить [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] пропускать уже актуальные пакеты элементов.  
  
## <a name="batching-targets"></a>Целевые объекты пакетной обработки  
 Следующий пример содержит список элементов `Res`, который поделен на два пакета на основе метаданные элемента `Culture`. Каждый из пакетов передается в задачу `AL`, которая создает для них по выходной сборке. Используя пакетную обработку для атрибута `Outputs` элемента `Target`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] может определить, актуальны ли отдельные пакеты, прежде чем запускать целевой объект. Без пакетной обработки целевых объектов оба пакета элементов будут выполняться задачей при каждом запуске целевого объекта.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Инкрементная сборка](../msbuild/how-to-build-incrementally.md)   
 [Пакетная обработка](../msbuild/msbuild-batching.md)   
 [Элемент Target (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Метаданные элементов в пакетной обработке задач](../msbuild/item-metadata-in-task-batching.md)




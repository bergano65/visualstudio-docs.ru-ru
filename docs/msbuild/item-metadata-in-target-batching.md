---
title: Метаданные элементов в пакетной обработке целевых объектов | Документы Майкрософт
description: Узнайте, как MSBuild использует метаданные элемента при пакетной обработке целей для анализа зависимостей входных и выходных данных цели сборки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d3389d24ded805c7b1f8bbb8d31daef0cbef1a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913911"
---
# <a name="item-metadata-in-target-batching"></a>Метаданные элементов в пакетной обработке целевых объектов

MSBuild может анализировать зависимости для входных и выходных данных целевого объекта сборки. Если определено, что входные или выходные данные целевого объекта актуальны, он пропускается, а сборка продолжается. Элементы `Target` используют атрибуты `Inputs` и `Outputs`, чтобы задать элементы, обрабатываемые во время анализа зависимостей.

Если целевой объект содержит задачу, которая использует пакетные элементы в качестве входных и выходных данных, элемент `Target` целевого объекта должен использовать пакетную обработку в своих атрибутах `Inputs` или `Outputs`, чтобы позволить MSBuild пропускать уже актуальные пакеты элементов.

## <a name="batch-targets"></a>Целевые объекты пакетной службы

Следующий пример содержит список элементов `Res`, который поделен на два пакета на основе метаданные элемента `Culture`. Каждый из пакетов передается в задачу `AL`, которая создает для них по выходной сборке. Используя пакетную обработку для атрибута `Outputs` элемента `Target`, MSBuild может определить, актуальны ли отдельные пакеты, прежде чем запускать целевой объект. Без пакетной обработки целевых объектов оба пакета элементов будут выполняться задачей при каждом запуске целевого объекта.

```xml
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
            OutputAssembly="%(Culture)\MyApp.resources.dll">

    </Target>

</Project>
```

## <a name="see-also"></a>См. также раздел

- [Практическое руководство. Инкрементная сборка](../msbuild/how-to-build-incrementally.md)
- [Пакетная обработка в MSBuild](../msbuild/msbuild-batching.md)
- [Элемент Target (MSBuild)](../msbuild/target-element-msbuild.md)
- [Метаданные элементов в пакетной обработке задач](../msbuild/item-metadata-in-task-batching.md)

---
title: Как выполнить Расширение процесса построения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 43b95fd47c2d5b859478814dd330c175e82bac89
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758669"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Как выполнить Расширение процесса построения Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Процесс сборки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] определяется рядом TARGETS-файлов [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], которые импортируются в файл проекта. Один из этих импортированных файлов — Microsoft.Common.targets — можно расширить, чтобы выполнять настраиваемые задачи в нескольких точках в процессе сборки. Этот раздел описывает два метода, которые можно использовать для расширения процесса сборки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:

-   Переопределение конкретных предварительно заданных целевых объектов, определенных в Microsoft.Common.targets.

-   Переопределение свойств "DependsOn", определенных в Microsoft.Common.targets.

## <a name="overriding-predefined-targets"></a>Переопределение предопределенных целевых объектов
 Файл Microsoft.Common.targets содержит ряд предопределенных пустых целевых объектов, которые вызываются до и после некоторых основных целевых объектов в процессе сборки. Например, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] вызывает целевой объект `BeforeBuild` перед основным целевым объектом `CoreBuild`, а целевой объект `AfterBuild` — после целевого объекта `CoreBuild`. По умолчанию пустые целевые объекты в Microsoft.Common.targets не выполняют никаких действий, но их поведение по умолчанию можно переопределить, определив нужные целевые объекты в файле проекта, куда импортируется файл Microsoft.Common.targets. Таким образом, вы можете использовать задачи [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], чтобы получить больший контроль над процессом сборки.

#### <a name="to-override-a-predefined-target"></a>Переопределение предопределенного целевого объекта

1. Выберите в Microsoft.Common.targets предварительно заданный целевой объект, который требуется переопределить. Приведенная ниже таблица содержит полный список целевых объектов, которые можно безопасно переопределить.

2. Определите один или несколько целевых объектов в конце файла проекта, прямо перед тегом `</Project>`. Например:

   ```
   <Project>
       ...
       <Target Name="BeforeBuild">
           <!-- Insert tasks to run before build here -->
       </Target>
       <Target Name="AfterBuild">
           <!-- Insert tasks to run after build here -->
       </Target>
   </Project>
   ```

3. Выполните сборку файла проекта.

   Следующая таблица показывает все целевые объекты в Microsoft.Common.targets, которые можно безопасно переопределить.

|Целевое имя|Описание|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после основной компиляции. Основная часть настроек выполняется в одном из этих двух целевых объектов.|
|`BeforeBuild`, `AfterBuild`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после остальной части сборки. **Примечание.**  `BeforeBuild` И `AfterBuild` целевых объектов уже определены в комментариях в конце большинства файлов проекта. Это позволяет легко добавлять в файл проекта события, возникающие до и после сборки.|
|`BeforeRebuild`, `AfterRebuild`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после вызова основной функции перестроения. В Microsoft.Common.targets действует следующий порядок выполнения целевых объектов: `BeforeRebuild`, `Clean`, `Build`, а затем `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после вызова основной функции очистки.|
|`BeforePublish`, `AfterPublish`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после вызова основной функции публикации.|
|`BeforeResolveReference`, `AfterResolveReferences`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после разрешения ссылок на сборки.|
|`BeforeResGen`, `AfterResGen`|Задачи, добавленные в один из этих целевых объектов, выполняются до или после создания ресурсов.|

## <a name="overriding-dependson-properties"></a>Переопределение свойств "DependsOn"
 Переопределение предопределенных целевых объектов позволяет легко расширить процесс сборки, но так как [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] оценивает определение целевых объектов последовательно, не существует способа запретит другому проекту, который импортирует ваш проект, переопределить целевые объекты, которые вы уже переопределили. Например, последний целевой объект `AfterBuild`, определенный в файле проекта, после импорта всех остальных проектов будет использоваться в процессе сборки.

 Вы можете предусмотреть защиту от нежелательных переопределений целевых объектов, переопределив свойства "DependsOn", которые используются в атрибутах `DependsOnTargets` по всему файлу Microsoft.Common.targets. Например, целевой объект `Build` содержит значение атрибута `DependsOnTargets`, равное `"$(BuildDependsOn)"`. Рассмотрим этот пример:

```
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

 Этот фрагмент XML-кода указывает, что перед выполнением целевого объекта `Build` должны быть выполнены все целевые объекты, указанные в свойстве `BuildDependsOn`. Свойство `BuildDependsOn` определено следующим образом:

```
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

 Значение этого свойства можно переопределить, объявив другое свойство с именем `BuildDependsOn` в конце файла проекта. Включив предыдущее свойство `BuildDependsOn` в новое, можно добавить новые целевые объекты в начало и конец списка целевых объектов. Например:

```
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

 Проекты, импортирующие ваши файлы проекта, могут переопределить эти свойства, не переопределяя внесенные вами настройки.

#### <a name="to-override-a-dependson-property"></a>Переопределение свойства "DependsOn"

1.  Выберите в Microsoft.Common.targets предварительно заданное свойство "DependsOn", которое требуется переопределить. Приведенная ниже таблица содержит список часто переопределяемых свойств "DependsOn".

2.  Определите еще один экземпляр свойства или свойств в конце файла проекта. Включите исходное свойство, например `$(BuildDependsOn)`, в новое свойство.

3.  Определите пользовательские целевые объекты до или после определения свойства.

4.  Выполните сборку файла проекта.

### <a name="commonly-overridden-dependson-properties"></a>Часто переопределяемые свойства "DependsOn"

|Имя свойства|Описание|
|-------------------|-----------------|
|`BuildDependsOn`|Свойство, которое следует переопределить, если нужно вставить пользовательские целевые объекты до или после всего процесса сборки.|
|`CleanDependsOn`|Свойство, которое следует переопределить, если нужно убрать выходные данные из пользовательского процесса сборки.|
|`CompileDependsOn`|Свойство, которое следует переопределить, если нужно вставить пользовательские процессы до или после этапа компиляции.|

## <a name="see-also"></a>См. также раздел
 [Интеграция с Visual Studio](../msbuild/visual-studio-integration-msbuild.md) [основные возможности MSBuild](../msbuild/msbuild-concepts.md) [. Файлы целевых объектов](../msbuild/msbuild-dot-targets-files.md)

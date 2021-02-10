---
title: Практическое руководство. Сборка проекта, содержащего ресурсы | Документация Майкрософт
description: Узнайте, как создать проект с ресурсами и как компилировать ресурсы с помощью MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 195ef17e4770d7050bc3b10f11ca5530e5ca49cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914484"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Практическое руководство. Построение проекта, содержащего ресурсы

При создании локализованных версий проекта все элементы пользовательского интерфейса должны разделяться по файлам ресурсов для разных языков. Если в проекте используются только строки, в качестве файлов ресурсов могут выступать текстовые файлы. Кроме того, в этих целях можно использовать *RESX*-файлы.

## <a name="compile-resources-with-msbuild"></a>Компиляция ресурсов с помощью MSBuild

Библиотека общих задач, предоставляемая вместе с MSBuild, включает в себя задачу `GenerateResource`, позволяющую компилировать ресурсы в *RESX*-файлах или текстовых файлах. Эта задача включает параметр `Sources` для указания компилируемых файлов ресурсов и параметр `OutputResources` для указания имен выходных файлов ресурсов. Дополнительные сведения о задаче `GenerateResource` см. в разделе [Задача GenerateResource](../msbuild/generateresource-task.md).

#### <a name="to-compile-resources-with-msbuild"></a>Компиляция ресурсов с помощью MSBuild

1. Определите файлы ресурсов проекта и передайте их в задачу `GenerateResource` в виде списков элементов или имен файлов.

2. Укажите параметр `OutputResources` задачи `GenerateResource`, позволяющий задать имена выходных файлов ресурсов.

3. Используйте элемент `Output` задачи, чтобы сохранить значение параметра `OutputResources` в элементе.

4. Используйте элемент, созданный из элемента `Output`, в качестве входных данных для другой задачи.

## <a name="example-1"></a>Пример 1

В следующем примере кода показано, как элемент `Output` указывает, что атрибут `OutputResources` задачи `GenerateResource` будет содержать скомпилированные файлы ресурсов *alpha.resources* и *beta.resources*, и что эти два файла будут помещены в список элементов `Resources`. Определив эти файлы *RESOURCES* как коллекцию элементов с таким же именем, вы можете легко использовать их в качестве входных данных для другой задачи, например [Csc](../msbuild/csc-task.md).

Эта задача аналогична использованию параметра **/compile** для программы [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):

`Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`

```xml
<GenerateResource
    Sources="alpha.resx; beta.txt"
    OutputResources="alpha.resources; beta.resources">
    <Output TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

## <a name="example-2"></a>Пример 2

Приведенный ниже пример проекта содержит две задачи: задача `GenerateResource` для компиляции ресурсов и задача `Csc` для компиляции как файлов исходного кода, так и скомпилированных файлов ресурсов. Файлы ресурсов, скомпилированные задачей `GenerateResource`, хранятся в элементе `Resources` и передаются задаче `Csc`.

```xml
<Project DefaultTargets = "Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <Target Name="Resources">
        <GenerateResource
            Sources="alpha.resx; beta.txt"
            OutputResources="alpha.resources; beta.resources">
            <Output TaskParameter="OutputResources"
                ItemName="Resources"/>
        </GenerateResource>
    </Target>

    <Target Name="Build" DependsOnTargets="Resources">
        <Csc Sources="hello.cs"
                Resources="@(Resources)"
                OutputAssembly="hello.exe"/>
    </Target>
</Project>
```

## <a name="see-also"></a>См. также

- [MSBuild](../msbuild/msbuild.md)
- [GenerateResource - задача](../msbuild/generateresource-task.md)
- [Задача Csc](../msbuild/csc-task.md)
- [Resgen.exe (генератор файлов ресурсов)](/dotnet/framework/tools/resgen-exe-resource-file-generator)

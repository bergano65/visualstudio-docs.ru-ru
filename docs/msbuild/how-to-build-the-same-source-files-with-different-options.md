---
title: Сборка одинаковых исходных файлов с различными параметрами
description: Сведения о том, как создавать различные конфигурации сборки MSBuild для создания одних и тех же исходных файлов с разными параметрами.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bd9d77e32f9c287ac2dfcf3905fe9335e119a3a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914499"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Практическое руководство. Построение одинаковых исходных файлов с различными параметрами

При сборке проектов вы часто компилируете одни и те же компоненты с разными параметрами сборки. Например, вы можете создать отладочную сборку с символьной информацией или сборку выпуска без такой информации, но с включенными оптимизациями. Можно также создать проект для выполнения на определенной платформе, например x86 или x64. Во всех этих случаях основная часть параметров сборки остается без изменений, а управление конфигурацией сборки осуществляется с помощью всего нескольких параметров. MSBuild позволяет использовать свойства и условия для создания различных конфигураций сборки.

## <a name="use-properties-to-control-build-settings"></a>Использование свойств для управления параметрами сборки

Элемент `Property` определяет переменную, на которую имеется несколько ссылок в файле проекта, например, расположение временного каталога, или значения для свойств, используемых в нескольких конфигурациях, таких как отладочная сборка и сборка выпуска. Дополнительные сведения о свойствах см. в разделе [Свойства MSBuild](../msbuild/msbuild-properties.md).

Свойства можно использовать для изменения конфигурации сборки без редактирования файла проекта. Атрибут `Condition` элемента `Property` и элемент `PropertyGroup` позволяют изменять значения свойств. Дополнительные сведения об условиях MSBuild см. в разделе [Условия](../msbuild/msbuild-conditions.md).

### <a name="to-set-a-group-of-properties-that-depends-on-another-property"></a>Задание группы свойств, которые зависят от другого свойства

- Используйте атрибут `Condition` в элементе `PropertyGroup` по аналогии со следующей процедурой:

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

### <a name="to-define-a-property-that-depends-on-another-property"></a>Определение свойства, которое зависит от другого свойства

- Используйте атрибут `Condition` в элементе `Property` по аналогии со следующей процедурой:

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>Указание свойств в командной строке

После составления такого файла проекта, который поддерживает несколько конфигураций, вам нужна возможность изменять эти конфигурации при сборке проекта. MSBuild предоставляет такую возможность, позволяя указывать свойства в командной строке с помощью параметра **-property** или **-p**.

### <a name="to-set-a-project-property-at-the-command-line"></a>Задание свойства проекта в командной строке

- Используйте параметр **-property** с указанием свойства и его значения. Пример:

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  или диспетчер конфигурации служб

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Задание нескольких свойств проекта в командной строке

- Используйте параметр **-property** или **-p** с указанием свойств и их значений либо используйте один параметр **-property** или **-p**, указав несколько свойств через точку с запятой (;). Пример:

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  или диспетчер конфигурации служб

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  Переменные среды также обрабатываются как свойства и автоматически внедряются MSBuild. Дополнительные сведения об использовании переменных среды см. в разделе [Практическое руководство. Использование переменных среды в построении](../msbuild/how-to-use-environment-variables-in-a-build.md).

  Значение свойства, которое указано в командной строке, имеет приоритет над любым значением для того же свойства, заданным в файле проекта, а значение в файле проекта имеет приоритет над значением в переменной среды.

  Это поведение можно изменить с помощью атрибута `TreatAsLocalProperty` в теге проекта. Для имен свойств, которые указаны с использованием этого атрибута, значение свойства, заданное в командной строке, не имеет приоритет над значением в файле проекта. См. пример далее в этом разделе.

## <a name="example-1"></a>Пример 1

В следующем примере кода проект Hello World содержит две новых группы свойств, которые можно использовать для создания отладочной сборки и сборки выпуска.

Чтобы создать отладочную версию проекта, введите:

```cmd
msbuild consolehwcs1.proj -p:flavor=debug
```

Чтобы создать розничную версию проекта, введите:

```cmd
msbuild consolehwcs1.proj -p:flavor=retail
```

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Sets the default flavor if an environment variable called
    Flavor is not set or specified on the command line -->
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
    </PropertyGroup>

    <!-- Define the DEBUG settings -->
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
        <DebugType>full</DebugType>
        <Optimize>no</Optimize>
    </PropertyGroup>

    <!-- Define the RETAIL settings -->
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">
        <DebugType>pdbonly</DebugType>
        <Optimize>yes</Optimize>
    </PropertyGroup>

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files
        of type CSFile -->
        <CSC  Sources = "@(CSFile)"
            DebugType="$(DebugType)"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe" >

            <!-- Set the OutputAssembly attribute of the CSC
            task to the name of the executable file that is
            created -->
            <Output TaskParameter="OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example-2"></a>Пример 2

В следующем примере показано использование атрибута `TreatAsLocalProperty`. Свойство `Color` имеет значение `Blue` в файле проекта и `Green` в командной строке. Так как в теге проекта указано `TreatAsLocalProperty="Color"`, свойство командной строки (`Green`) не переопределяется свойство, заданное в файле проекта (`Blue`).

Чтобы выполнить сборку проекта, введите следующую команду:

```cmd
msbuild colortest.proj -t:go -property:Color=Green
```

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0" TreatAsLocalProperty="Color">

    <PropertyGroup>
        <Color>Blue</Color>
    </PropertyGroup>

    <Target Name="go">
        <Message Text="Color: $(Color)" />
    </Target>
</Project>

<!--
  Output with TreatAsLocalProperty="Color" in project tag:
     Color: Blue

  Output without TreatAsLocalProperty="Color" in project tag:
     Color: Green
-->
```

## <a name="see-also"></a>См. также

- [MSBuild](../msbuild/msbuild.md)
- [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Элемент Project (MSBuild)](../msbuild/project-element-msbuild.md)

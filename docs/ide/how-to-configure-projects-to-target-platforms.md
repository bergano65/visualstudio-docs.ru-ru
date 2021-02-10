---
title: Практическое руководство. настройку целевых платформ в проектах
description: Узнайте, как Visual Studio позволяет настраивать приложения для различных платформ, включая 64-разрядные платформы.
ms.custom: SEO-VS-2020
ms.date: 08/16/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f8a298f19f247c45740e87074804755f6ca691ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969871"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Практическое руководство. настройку целевых платформ в проектах

Visual Studio позволяет настраивать приложения для различных платформ, включая 64-разрядные платформы. Дополнительные сведения о поддержке 64-разрядных платформ в Visual Studio см. в статье [64-разрядные приложения](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Нацеливание на платформы с помощью диспетчера конфигураций

**Диспетчер конфигураций** позволяет быстро добавить новую платформу для нацеливания проекта. Если выбрать одну из платформ, входящих в Visual Studio, свойства проекта изменяются для сборки проекта в соответствии с выбранной платформой.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Настройка проекта для 64-разрядной платформы

1. В строке меню последовательно выберите пункты **Сборка** > **Диспетчер конфигураций**.

2. В списке **Активная платформа решения** выберите 64-разрядную платформу для нацеливания решения, а затем нажмите кнопку **Закрыть**.

    1. Если нужная платформа не отображается в списке **Активная платформа решения**, выберите **Создать**.

         Откроется диалоговое окно **Создание платформы решения**.

    2. В списке **Введите или выберите новую платформу** выберите **x64**.

        > [!NOTE]
        > Если вы присваиваете конфигурации новое имя, может потребоваться изменить параметры в **конструкторе проектов** для нацеливания на соответствующую платформу.

    3. Если требуется скопировать параметры из текущий конфигурации платформы, выберите ее и нажмите кнопку **ОК**.

Обновляются свойства для всех проектов, нацеленных на 64-разрядную платформу, и следующая сборка проекта будет оптимизирована под 64-разрядные платформы.

> [!NOTE]
> Имя платформы **Win32** используется для проектов C++ и соответствует **x86**. Visual Studio поддерживает платформы уровня проекта и платформы уровня решения. При этом платформы проекта основаны на системах проектов для разных языков. Проекты C++ используют **Win32** и **x64**, а платформы решения — **x86** и **x64**. Когда вы выбираете **x86** в качестве конфигурации решения, Visual Studio выбирает для проектов C++ платформу **Win32**. Чтобы просмотреть параметры платформы уровня проекта и платформы уровня решения, откройте **Configuration Manager** и обратите внимание на два параметра платформы. Платформа уровня решения отображается в раскрывающемся списке **Активная платформа решения**, а платформа уровня проекта показана в таблице для каждого проекта.
> ![Снимок экрана: платформа решения и платформа проекта](media/project-platform-win32.png)

## <a name="target-platforms-in-the-project-designer"></a>Нацеливание на платформы в конструкторе проектов

**Конструктор проектов** также предоставляет способ нацеливания проекта на различные платформы. Если выбор одной из платформ в списке диалогового окна **Создание платформы решения** не подходит для вашего решения, можно создать пользовательское имя конфигурации и изменить параметры в **конструкторе проектов** для нацеливания на соответствующую платформу.

Способ выполнения этой задачи зависит от используемого языка программирования. Дополнительные сведения см. на следующих страницах:

- Для проектов [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] см. раздел [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Для проектов [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] см. статью [Страница "Сборка", конструктор проектов (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Для проектов [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] см. статью [/clr (компиляция CLR)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="manually-editing-the-project-file"></a>Изменение файла проекта вручную

Иногда необходимо вручную изменить файл проекта, чтобы выполнить ряд пользовательских настроек. Это бывает нужно сделать, к примеру, при наличии условий, которые не могут быть указаны в интегрированной среде разработки (ссылка, имеющая разный вид для двух разных платформ, как показано в следующем примере).

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Пример. Ссылки на сборки x86 и x64 и библиотеки DLL

У вас может быть сборка .NET или библиотека DLL с версиями x86 и x64. Чтобы настроить проект для использования этих ссылок, сначала добавьте ссылку, а затем откройте файл проекта и измените его, чтобы добавить `ItemGroup` с условием, которое ссылается как на конфигурацию, так и на целевую платформу.  Например, предположим, что вы ссылаетесь на двоичный файл ClassLibrary1, и существуют разные пути для конфигураций отладки и выпуска, а также версии x86 и x64.  Используйте четыре элемента `ItemGroup` со всеми сочетаниями параметров, как показано далее:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
    <Platforms>AnyCPU;x64;x86</Platforms>
  </PropertyGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
  
  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
</Project>
```

::: moniker range="vs-2017"
> [!NOTE]
> Перед изменением файла проекта в Visual Studio 2017 сначала необходимо выгрузить проект. Для этого щелкните узел проекта правой кнопкой мыши и выберите пункт **Выгрузить проект**. После редактирования сохраните изменения и перезагрузите проект, щелкнув правой кнопкой мыши узел проекта и выбрав пункт **Перезагрузить проект**.
::: moniker-end

Дополнительные сведения о файле проекта см. в статье [Справочные сведения о схеме файлов проектов MSBuild](../msbuild/msbuild-project-file-schema-reference.md).

## <a name="see-also"></a>См. также

- [Общие сведения о платформах построения](../ide/understanding-build-platforms.md)
- [/platform (параметры компилятора C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64-разрядные приложения](/dotnet/framework/64-bit-apps)
- [Поддержка 64-разрядных сред IDE Visual Studio](../ide/visual-studio-ide-64-bit-support.md)
- [Общие сведения о файле проекта](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)

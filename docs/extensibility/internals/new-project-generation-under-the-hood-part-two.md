---
title: 'Создание проекта: Это работает, часть 2 | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ccdd4cd8bafc4bc4a899ea47d62ec10e578569c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909318"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Создание проекта: как это работает, часть 2

В [Создание нового проекта: За кулисами, часть первая](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) мы узнали, каким образом **новый проект** диалоговое окно, окно заполняется. Предположим, что вы выбрали **приложение Windows Visual C#**, заполненный **имя** и **расположение** текстовые поля и щелчка OK.

## <a name="generating-the-solution-files"></a>Создание файлов решения
 Выбрав шаблон приложения направляет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] распаковка и открытие соответствующих VSTEMPLATE-файл и запустить шаблон для интерпретации команд XML в этом файле. Эти команды создают проектов и элементов проектов в новом или существующем решении.

 Шаблон распаковывает источника файлы, называемые шаблоны элементов, из той же папки ZIP-файл, содержащий VSTEMPLATE-файл. Этот шаблон копирует эти файлы в новый проект, настройка их соответствующим образом.

### <a name="template-parameter-replacement"></a>Замена параметров шаблона
 Когда шаблон копирует шаблон элемента в новый проект, он заменяет любые параметры шаблона строк в файле. Параметр шаблона — это специальный маркер, и после идти знак доллара, например, $date$.

 Давайте взглянем на типичный проект шаблона элемента. Извлечь и изучить Program.cs в папке Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace $safeprojectname$
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

При создании нового проекта приложения Windows с именем Simple, он заменяет `$safeprojectname$` параметр с именем проекта.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace Simple
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

 Полный список параметров шаблона см. в разделе [Параметры шаблона](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Взгляните изнутри. Файл VSTemplate
 Формат имеет базовый VSTEMPLATE-файл

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Мы рассмотрели \<TemplateData > статьи [Создание нового проекта: Это работает, часть один](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Теги в этом разделе используются для управления внешним видом **новый проект** диалоговое окно.

 Теги в \<TemplateContent > раздел элемента управления, создание новых проектов и элементов проекта. Вот \<TemplateContent > раздел cswindowsapplication.vstemplate-файла в папке 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip \Program Files\Microsoft Visual Studio.

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
      Settings.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">
      Form1.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Form1.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Program.cs
    </ProjectItem>
  </Project>
</TemplateContent>
```

 \<Проекта > тег контролирует Создание проекта и \<ProjectItem > тег контролирует Создание элемента проекта. Если параметр ReplaceParameters имеет значение true, шаблон будет настраивать все параметры шаблона в файле проекта или элемента. В этом случае все элементы проекта настроены, за исключением Settings.settings.

 Параметр TargetFileName указывает имя и относительный путь, полученный файл проекта или элемента. Это позволяет создавать структуру папок для вашего проекта. Если не указать этот аргумент, элемент проекта будет иметь имя, совпадающее с именем шаблона элемента проекта.

 Итоговый структуру папок приложения Windows выглядит следующим образом:

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 Первая и единственная \<проекта > тег в операции чтения шаблона:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Это указывает, что шаблон нового проекта для создания файла проекта Simple.csproj путем копирования и настройка windowsapplication.csproj элемента шаблона.

### <a name="designers-and-references"></a>Конструкторы и ссылки
 Вы увидите в обозревателе решений, что папке "Свойства" присутствует и содержит ожидаемые файлы. Но как насчет проект ссылается на и файл конструктора зависимости, такие как Resources.Designer.cs для Resources.resx и Form1.Designer.cs, чтобы Form1.cs?  Они определяются в файле Simple.csproj при его создании.

 Вот \<ItemGroup > из Simple.csproj, которая создает ссылки на проект:

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 Вы увидите, что это шесть ссылки, которые отображаются в обозревателе решений. Ниже приведен раздел из другого \<ItemGroup >. Количество строк кода были удалены для ясности. В этом разделе ставит Settings.Designer.cs зависимость от Settings.settings:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>См. также

- [Создание проекта: как это работает, часть 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
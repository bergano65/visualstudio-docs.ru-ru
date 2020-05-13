---
title: 'Новое поколение проекта: Под капотом, часть вторая (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8692f2012e5f2733982f04e35a7fed415e49c636
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707021"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Создание нового проекта. Как это работает, часть 2

В [новом проекте поколения: под капотом, часть первая](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) мы видели, как **новый проект** диалог Box заселен. Предположим, что вы выбрали **приложение для Windows Visual C',** заполнили текстовые ящики **с именами** и **местоположениеми** и нажали OK.

## <a name="generating-the-solution-files"></a>Создание файлов решений
 Выбор шаблона приложения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] направляет на распаковку и открытие соответствующего файла .vstemplate, а также на запуск шаблона для интерпретации команд XML в этом файле. Эти команды создают проекты и элементы проекта в новом или существующем решении.

 Шаблон распаковывает исходные файлы, называемые шаблонами элементов, из той же папки .zip, в мещавей которого находится файл .vstemplate. Шаблон копирует эти файлы в новый проект, настраивая их соответствующим образом.

### <a name="template-parameter-replacement"></a>Замена параметра шаблона
 Когда шаблон копирует шаблон элемента для нового проекта, он заменяет любые параметры шаблона строками для настройки файла. Параметр шаблона — это специальный токен, который предшествует и сопровождается знаком доллара, например, $date$.

 Рассмотрим типичный шаблон элемента проекта. Извлеките и изучите Program.cs в папке «Файлы» (Microsoft Visual Studio) 8-Common7-IDE-ProjectTemplates-CSharp-Windows-1033-WindowsApplication.zip.zip.

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

При создании нового проекта приложения Windows под названием `$safeprojectname$` Simple шаблон заменяет параметр названием проекта.

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

## <a name="a-look-inside-a-vstemplate-file"></a>Взгляд внутрь . Файл VSTemplate
 Базовый файл .vstemplate имеет этот формат

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Мы рассмотрели \<раздел TemplateData> в [новом поколении проекта: Под капотом, часть первая](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Теги в этом разделе используются для управления внешним видом диалогового окна **нового проекта.**

 Теги в \<разделе TemplateContent> контролировать генерацию новых проектов и элементов проекта. Вот \<раздел TemplateContent> из файла cswindowsapplication.vstemplate в папке «Файлы программы» Microsoft Visual Studio 8»Common7-IDE-ProjectTemplates,CSharp-Windows-1033»WindowsApplication.zip.zip.

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

 Тег \<project> управляет генерацией проекта, \<а тег ProjectItem> управляет генерацией элемента проекта. Если параметр ReplaceParameters верен, шаблон будет настраивать все параметры шаблона в файле проекта или элементе. В этом случае все элементы проекта настроены, за исключением Settings.settings.

 Параметр TargetFileName определяет имя и относительный путь полученного файла или элемента проекта. Это позволяет создать структуру папок для вашего проекта. Если вы не укажете этот аргумент, элемент проекта будет иметь то же имя, что и шаблон элемента проекта.

 Полученная структура папки приложений Windows выглядит следующим образом:

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 Первый и \<единственный тег> Project в шаблоне гласит:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Это поручает шаблону Нового проекта создать файл проекта Simple.csproj путем копирования и настройки элемента шаблона windowsapplication.csproj.

### <a name="designers-and-references"></a>Дизайнеры и справочники
 В папке «Разновидец решений» можно увидеть, что папка «Свойства» присутствует и содержит ожидаемые файлы. Но как насчет ссылок на проекты и зависимостей от файлов-дизайнеров, таких как Resources.Designer.cs на Resources.resx и Form1.Designer.cs Form1.cs?  Они настроены в файле Simple.csproj при его сгенерировании.

 Вот \<> ItemGroup от Simple.csproj, который создает ссылки проекта:

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

 Вы можете видеть, что это шесть ссылок проекта, которые отображаются в Solution Explorer. Вот раздел из другого \<> ItemGroup. Многие строки кода были удалены для ясности. Этот раздел делает Settings.Designer.cs зависимым от settings.settings:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>См. также

- [Создание нового проекта. Как это работает, часть 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)

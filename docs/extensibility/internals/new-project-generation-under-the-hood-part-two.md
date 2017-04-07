---
title: "Создание нового проекта: За кулисами, часть | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5581224b17a7b42f65b69f741f984a144d78fc26
ms.openlocfilehash: 859eeac9c2fd322dcf231e9c70fe83b92b099111
ms.lasthandoff: 04/04/2017

---
# <a name="new-project-generation-under-the-hood-part-two"></a>Создание нового проекта: За кулисами, часть 2
В [Создание нового проекта: В механизме, часть 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) мы узнали, как **новый проект** диалоговое окно заполняется значениями. Предположим, что вы выбрали **приложения Windows Visual C#**, заполненных **имя** и **расположение** текстовые поля и выборе ОК.  
  
## <a name="generating-the-solution-files"></a>Создание файлов решения  
 Выбор шаблона приложения направляет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] распаковка и открытие соответствующего VSTEMPLATE-файл и для запуска шаблона для интерпретации команд XML в этом файле. Эти команды создают проектов и элементов проектов в новом или существующем решении.  
  
 Шаблон распаковывает источника файлов, называемых шаблонов элементов из той же папки расширением ZIP, содержащий VSTEMPLATE-файл. Шаблон копирует эти файлы в новый проект, настройка их соответствующим образом. Обзор шаблонов проектов и элементов см. в разделе [NIB: шаблоны Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041).  
  
### <a name="template-parameter-replacement"></a>Замена параметров шаблона  
 Когда шаблон копирует шаблона элемента в новый проект, он заменяет любые параметры шаблона строк в файле. Параметр шаблона — это специальный маркер, который является и стоять знак доллара, например $date$.  
  
 Рассмотрим типичный шаблон элемента. Извлечение и изучите Program.cs в папке Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.  
  
```  
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
  
```  
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
  
 Полный список параметров шаблона см. в разделе [параметров шаблона](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Вид внутри. Файл VSTemplate  
 Формат имеет базовый VSTEMPLATE-файл  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Мы рассмотрели \<TemplateData настроек статьи [Создание нового проекта: В механизме, часть 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Теги в этом разделе используются для управления внешним видом **новый проект** диалоговое окно.  
  
 Теги в \<TemplateContent настроек раздел управления создание новых проектов и элементов проектов. Вот \<TemplateContent настроек раздел cswindowsapplication.vstemplate-файла в папке 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip \Program Files\Microsoft Visual Studio.  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
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
  
 \<Проекта настроек тег контролирует Создание проекта и \<ProjectItem настроек тег контролирует Создание элемента проекта. Если параметр ReplaceParameters имеет значение true, шаблон будет выполнена настройка всех параметров шаблона в файле проекта или элемента. В этом случае все элементы проекта создаются пользователем, за исключением Settings.settings.  
  
 Параметр TargetFileName указывает имя и относительный путь, полученный файл проекта или элемента. Это позволяет создать структуру папок для проекта. Если этот аргумент не указан, элемент проекта будет иметь имя, совпадающее с именем шаблона элемента проекта.  
  
 Полученный Windows приложения выглядит следующим образом:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 Первым и единственным \<проекта настроек тег в операции чтения шаблона:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Это указывает, что шаблон нового проекта для создания файла проекта Simple.csproj путем копирования и настройка windowsapplication.csproj элемента шаблона.  
  
### <a name="designers-and-references"></a>Конструкторы и ссылки  
 Появится в обозревателе решений папку свойства существует и содержит ожидаемые файлы. Но что насчет проект ссылается на и файл конструктора зависимостей, таких как местоположении Resources.resx для Resources.resx и Form1.Designer.cs для Form1.cs?  Они настраиваются в файле Simple.csproj при его создании.  
  
 Вот \<ItemGroup настроек из Simple.csproj, которая создает ссылки на проект:  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 Вы увидите, что они ссылки шесть проекта, которые отображаются в обозревателе решений. Ниже приведен раздел из другого \<ItemGroup настроек. Количество строк кода были удалены для ясности. В этом разделе делает Settings.Designer.cs зависимым от Settings.settings:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>См. также  
 [Создание нового проекта. Как это работает, часть 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)

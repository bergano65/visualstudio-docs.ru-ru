---
title: "Создание нового проекта: За кулисами, часть&2; | Документы Microsoft"
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c5f214774a5cf0aeb3896004632f8a2076782b14
ms.lasthandoff: 02/22/2017

---
# <a name="new-project-generation-under-the-hood-part-two"></a>Создание нового проекта: За кулисами, часть&2;
В [Создание нового проекта: под капот, часть&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) мы видели как **новый проект** диалоговое окно заполняется значениями. Предположим, вы выбрали **приложения Windows Visual C#**, заполненных **имя** и **расположение** текстовые поля и щелкните ОК.  
  
## <a name="generating-the-solution-files"></a>Создание файлов решения  
 Выбрав шаблон приложения направляет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Распакуйте и открывать соответствующие VSTEMPLATE-файл и запустить шаблон для интерпретации команд XML в этом файле. Эти команды создают проектов и элементов проектов в решение новый или существующий.  
  
 Шаблон распаковывает исходных файлов вызывается шаблоны элементов из той же папки .zip, содержащий VSTEMPLATE-файл. Шаблон копирует эти файлы в новый проект, настройка их соответствующим образом. Обзор шаблонов проектов и элементов см. в разделе [NIB: шаблоны Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041).  
  
### <a name="template-parameter-replacement"></a>Замена параметров шаблона  
 Когда шаблон копирует шаблон элемента проекта, он заменяет любые параметры шаблона строк в файле. Параметр шаблона — это специальный маркер, который начинается и затем знак доллара, например $date$.  
  
 Давайте взглянем на типичный шаблон элемента. Извлечение и просмотрите файл Program.cs в папке Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.  
  
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
  
 Полный список параметров шаблона см. в разделе [параметры шаблона](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Взгляните изнутри. VSTemplate-файл  
 Формат имеет базовый VSTEMPLATE-файла  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Мы рассмотрели \<TemplateData настроек статьи [Создание нового проекта: под капот, часть&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Теги в этом разделе используются для управления внешним видом **новый проект** диалоговое окно.  
  
 Теги в \<TemplateContent настроек раздел управления создания новых проектов и элементов проектов. Вот \<TemplateContent настроек раздел cswindowsapplication.vstemplate-файла в папку 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip Files\Microsoft Visual Studio.  
  
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
  
 \<Проекта настроек тег контролирует Создание проекта и \<ProjectItem настроек тег контролирует Создание элемента проекта. Если параметр ReplaceParameters имеет значение true, шаблон будет настраивать все параметры шаблона в файле проекта или элемента. В этом случае все элементы проекта настраиваются, за исключением Settings.settings.  
  
 TargetFileName параметр указывает имя и относительный путь, полученный файл проекта или элемента. Это позволяет создавать структуру папок для проекта. Если этот аргумент не указан, элемент проекта будет иметь имя, совпадающее с именем шаблона элемента проекта.  
  
 Полученный Windows приложение выглядит следующим образом:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 Первым и единственным \<проекта настроек тег в чтении шаблона:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Это указывает, что шаблон нового проекта для создания файла проекта Simple.csproj путем копирования и настройка windowsapplication.csproj элемента шаблона.  
  
### <a name="designers-and-references"></a>Конструкторы и ссылки  
 Вы увидите в обозревателе решений, в папке «свойства», содержащий предполагаемые файлы. Но как насчет проект ссылается на и файл конструктора зависимости, такие как Resources.Designer.cs для Resources.resx и Form1.Designer.cs, чтобы Form1.cs?  Они настраиваются в файле Simple.csproj при его создании.  
  
 Вот \<ItemGroup настроек из Simple.csproj, который создает ссылки проекта:  
  
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
  
 Вы увидите, что они шесть проекта ссылки, которые отображаются в обозревателе решений. Вот как выглядит раздел из другой \<ItemGroup настроек. Количество строк кода были удалены для ясности. В этом разделе делает Settings.Designer.cs зависимым от Settings.settings:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>См. также  
 [Создание нового проекта: За кулисами, часть&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild1.md)

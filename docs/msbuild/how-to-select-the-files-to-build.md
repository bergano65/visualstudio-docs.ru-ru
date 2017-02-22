---
title: "Практическое руководство. Выбор файлов для построения | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Include - атрибут [MSBuild]"
  - "MSBuild, включение файлов"
  - "MSBuild, подстановочные знаки"
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Практическое руководство. Выбор файлов для построения
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При создании проекта, содержащего несколько файлов, можно указывать каждый файл отдельно в файле проекта, а можно использовать знаки подстановки, чтобы включить все файлы в одном каталоге или наборе вложенных каталогов.  
  
## Указание входных данных  
 Входные данные для построения представлены в элементах.  Дополнительные сведения об элементах см. в разделе [Элементы](../msbuild/msbuild-items.md).  
  
 Чтобы включить файлы в построение, их необходимо включить в список элементов в файле проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Чтобы добавить в список элементов несколько файлов, можно включать файлы по отдельности или использовать знаки подстановки, чтобы включить несколько файлов одновременно.  
  
#### Объявление отдельных элементов  
  
-   Используйте атрибуты `Include` следующим образом:  
  
     `<CSFile Include="form1.cs"/>`  
  
     либо  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  Если элементы в коллекции элементов не находится в том же каталоге, что и файл проекта, необходимо указать полный или относительный путь к элементу.  Например, `Include="..\..\form2.cs"`.  
  
#### Объявление нескольких элементов  
  
-   Используйте атрибуты `Include` следующим образом:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     либо  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## Указание входных данных с помощью знаков подстановки  
 Знаки подстановки можно использовать для рекурсивного включения всех файлов или только определенных файлов из подкаталогов в качестве входных данных для построения.  Дополнительные сведения о подстановочных знаках см. в разделе [Элементы](../msbuild/msbuild-items.md).  
  
 В приведенных далее примерах за основу взят проект, в котором содержатся графические файлы в следующих каталогах и подкаталогах \(файл проекта находится в каталоге "Project"\):  
  
 Project\\Images\\BestJpgs  
  
 Project\\Images\\ImgJpgs  
  
 Project\\Images\\ImgJpgs\\Img1  
  
#### Включение всех JPG\-файлов в каталоге "Images" и подкаталогах  
  
-   Используйте следующий атрибут `Include`:  
  
     `Include="Images\**\*.jpg"`  
  
#### Включение всех JPG\-файлов, начинающихся со слога "img"  
  
-   Используйте следующий атрибут `Include`:  
  
     `Include="Images\**\img*.jpg"`  
  
#### Включение всех файлов в каталогах с именами, которые оканчиваются слогом "jpgs"  
  
-   Используйте один из следующих атрибутов `Include`:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     либо  
  
     `Include="Images\**\*jpgs\*"`  
  
## Передача элементов в задачу  
 В файле проекта используйте в задачах запись @\(\), чтобы указать весь список элементов в качестве входных данных для построения.  Эту запись можно использовать при перечислении файлов по отдельности или при использовании знаков подстановки.  
  
#### Использование всех файлов Visual C\# или Visual Basic в качестве входных данных  
  
-   Используйте атрибуты `Include` следующим образом:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     либо  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  Чтобы указать входные данные для построения, необходимо использовать знаки подстановки в элементах; нельзя указать входные данные с помощью атрибута `Sources` в задаче [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], такой как [Csc](../msbuild/csc-task.md) или [Vbc](../msbuild/vbc-task.md).  Следующий пример недопустим в файле проекта:  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## Пример  
 В приведенном ниже примере кода показан проект, в котором все входные файлы включены по отдельности.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Builtdir>built</Builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="Form1.cs"/>  
        <CSFile Include="AssemblyInfo.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## Пример  
 В приведенном ниже примере кода используется знак подстановки для включения всех CS\-файлов.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## См. также  
 [Практическое руководство. Исключение файлов из построения](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Элементы](../msbuild/msbuild-items.md)
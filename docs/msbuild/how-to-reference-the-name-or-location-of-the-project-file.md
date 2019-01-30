---
title: Как выполнить Использование ссылки на имя или расположение файла проекта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b39176faffba1f90b9f955662322b37fdfbe2b75
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027403"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Как выполнить Использование ссылки на имя или расположение файла проекта
Имя или расположение проекта в файле проекта можно использовать без создания отдельного свойства. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] предоставляет зарезервированные свойства, ссылающиеся на имя файла проекта, и другие свойства, связанные с проектом. Дополнительные сведения о зарезервированных свойствах см. в статье [Зарезервированные и стандартные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="use-the-project-properties"></a>Использование свойств проекта
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] предоставляет некоторые зарезервированные свойства, которые можно использовать в файлах проекта, не определяя их каждый раз. Например, зарезервированное свойство `MSBuildProjectName` предоставляет ссылку на имя файла проекта. Зарезервированное свойство `MSBuildProjectDirectory` предоставляет ссылку на расположение файла проекта.
  
#### <a name="to-use-the-project-properties"></a>Использование свойств проекта
  
- Укажите ссылка на свойство в файле проекта с помощью нотации $() так же, как и для любого свойства. Например:  
  
  ```xml  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```          
  
  Преимущество использования зарезервированного свойства заключается в том, что любые изменения имени файла проекта применяются автоматически. В следующий раз при сборке проекта выходной файл будет иметь новое имя, и это не потребует никаких дополнительных действий с вашей стороны.  
  
> [!NOTE]
>  Зарезервированные свойства нельзя переопределить в файле проекта.  
  
## <a name="example"></a>Пример  
 В следующем примере файл проекта ссылается на имя проекта как зарезервированное свойство, чтобы указать имя для выходных данных.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
     </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  

## <a name="example"></a>Пример
 В следующем примере файл проекта использует зарезервированное свойство `MSBuildProjectDirectory`, чтобы создать полный путь к файлу в расположении проекта.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">     
    
    <!-- Build the path to a file in the root of the project -->  
    <PropertyGroup>  
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
[MSBuild](../msbuild/msbuild.md)  
[Зарезервированные и стандартные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)

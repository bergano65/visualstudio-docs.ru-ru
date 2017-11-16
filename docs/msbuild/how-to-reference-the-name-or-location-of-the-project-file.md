---
title: "Практическое руководство. Использование ссылки на имя или расположение файла проекта | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: "13"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 9186b98b482b101254e70def9285d9bbad2ca254
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Практическое руководство. Использование ссылки на имя или расположение файла проекта
Имя или расположение проекта в файле проекта можно использовать без создания отдельного свойства. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] предоставляет зарезервированные свойства, ссылающиеся на имя файла проекта, и другие свойства, связанные с проектом. Дополнительные сведения о зарезервированных свойствах см. в статье [Зарезервированные и стандартные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Использование свойства MSBuildProjectName  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] предоставляет некоторые зарезервированные свойства, которые можно использовать в файлах проекта, не определяя их каждый раз. Например, зарезервированное свойство `MSBuildProjectName` предоставляет ссылку на имя файла проекта.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>Использование свойства MSBuildProjectName  
  
-   Укажите ссылка на свойство в файле проекта с помощью нотации $() так же, как и для любого свойства. Например:  
  
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
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
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
  
## <a name="see-also"></a>См. также  
[MSBuild](../msbuild/msbuild.md)  
 [Зарезервированные и стандартные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
---
title: "Практическое руководство. Построение проекта, содержащего ресурсы | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0ca7978c4b50794b0c165ce8251da989a1653364
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-build-a-project-that-has-resources"></a>Практическое руководство. Построение проекта, содержащего ресурсы
При создании локализованных версий проекта все элементы пользовательского интерфейса должны разделяться по файлам ресурсов для разных языков. Если в проекте используются только строки, в качестве файлов ресурсов могут выступать текстовые файлы. Кроме того, в этих целях можно использовать RESX-файлы.  
  
## <a name="compiling-resources-with-msbuild"></a>Компиляция ресурсов с помощью MSBuild  
 Библиотека общих задач, предоставляемая вместе с [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], включает в себя задачу `GenerateResource`, позволяющую компилировать ресурсы в RESX-файлах или текстовых файлах. Эта задача включает параметр `Sources` для указания компилируемых файлов ресурсов и параметр `OutputResources` для указания имен выходных файлов ресурсов. Дополнительные сведения о задаче `GenerateResource` см. в разделе [Задача GenerateResource](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Компиляция ресурсов с помощью MSBuild  
  
1.  Определите файлы ресурсов проекта и передайте их в задачу `GenerateResource` в виде списков элементов или имен файлов.  
  
2.  Укажите параметр `OutputResources` задачи `GenerateResource`, позволяющий задать имена выходных файлов ресурсов.  
  
3.  Используйте элемент `Output` задачи, чтобы сохранить значение параметра `OutputResources` в элементе.  
  
4.  Используйте элемент, созданный из элемента `Output`, в качестве входных данных для другой задачи.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано как элемент `Output` указывает, что атрибут `OutputResources` задачи `GenerateResource` будет содержать скомпилированные файлы ресурсов `alpha.resources` и `beta.resources`, и что эти два файла будет помещены в список элементов `Resources`. Определив эти файлы RESOURCES как коллекцию элементов с таким же именем, вы можете легко использовать их в качестве входных данных для другой задачи, например [Csc](../msbuild/csc-task.md).  
  
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
  
## <a name="example"></a>Пример  
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
[MSBuild](../msbuild/msbuild.md)  
 [Задача GenerateResource](../msbuild/generateresource-task.md)   
 [Задача Csc](../msbuild/csc-task.md)   
 [Resgen.exe (генератор файлов ресурсов)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
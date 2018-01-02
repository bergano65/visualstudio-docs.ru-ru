---
title: "Как использовать зарезервированные символы XML в файлах проектов | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: "14"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 8acc59afdd050998f2269cc9be1986b7f4f426ae
ms.sourcegitcommit: 38097344f3ff74ba7b03bcfa45910015ca6bc2be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2017
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Как использовать резервные символы XML в файлах проектов
При создании файлов проекта вам может потребоваться использовать зарезервированные символы XML, например, в значениях свойств или параметров задачи. Однако некоторые зарезервированные символы необходимо заменить именованными сущностями, чтобы файл проекта можно было проанализировать.  
  
## <a name="using-reserved-characters"></a>Использование зарезервированных символов  
 В следующей таблице описаны зарезервированные символы XML, которые требуется заменить именованными сущностями, чтобы файл проекта можно было проанализировать.  
  
|Зарезервированный символ|Именованная сущность|  
|------------------------|------------------|  
|\<|&amp;lt;|  
|>|&amp;gt;|  
|&|&amp;amp;|  
|"|&amp;quot;|  
|'|&amp;apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Использование двойных кавычек в файле проекта  
  
-   Замените двойные кавычки соответствующей именованной сущностью &amp;quot;. Например, чтобы заключить в двойные кавычки список элементов `EXEFile`, введите:  
  
    ```xml  
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>  
    ```  
  
## <a name="example"></a>Пример  
 В следующем примере кода двойные кавычки используются для выделения имени файла в сообщении, выводимом файлом проекта.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)    
 [MSBuild](../msbuild/msbuild.md)    

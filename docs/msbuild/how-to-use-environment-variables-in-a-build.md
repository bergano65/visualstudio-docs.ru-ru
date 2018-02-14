---
title: "Практическое руководство. Использование переменных среды в построении | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 246f13b340c0acea519dccd323c1e7b2c28dd344
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Практическое руководство. Использование переменных среды в построении
При сборке проектов часто бывает необходимо задать параметры сборки, используя сведения не из файла проекта или файлов, входящих в проект. Эти сведения обычно хранятся в переменных среды.  
  
## <a name="referencing-environment-variables"></a>Ссылки на переменные среды  
 Все переменные среды доступны файлу проекта [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) в виде свойств.  
  
> [!NOTE]
>  Если файл проекта содержит явное определение свойства с тем же именем, что и у переменной среды, свойство в файле проекте переопределяет значение переменной среды.  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Использование переменной среды в проекте MSBuild  
  
-   Ссылка на переменную среды выполняется аналогично объявлению переменной в файле проекта. Например, следующий код ссылается на переменную среды BIN_PATH:  
  
     `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
 Вы можете использовать атрибут `Condition`, чтобы предоставить значение по умолчанию для свойства, если переменная среды не задана.  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>Предоставление значения по умолчанию для свойства  
  
-   Используйте атрибут `Condition` для свойства, чтобы задать значение только в том случае, когда свойство не имеет значения. Например, следующий код задает для свойства `ToolsPath` значение c:\tools только тогда, когда переменная среды `ToolsPath` не задана:  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    >  Имена свойств не учитывают регистр, поэтому как `$(ToolsPath)`, так и `$(TOOLSPATH)` ссылаются на одно свойство или одну переменную среды.  
  
## <a name="example"></a>Пример  
 Следующий файл проекта использует переменные среды, чтобы указать расположение каталогов.  
  
```xml  
<Project DefaultTargets="FakeBuild">  
    <PropertyGroup>  
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>  
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">  
            C:\Tools  
        </ToolsPath>  
    </PropertyGroup>  
    <Target Name="FakeBuild">  
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
    [MSBuild ](../msbuild/msbuild.md)
    [MSBuild Properties](../msbuild/msbuild-properties.md)
 [Практическое руководство. Построение одинаковых исходных файлов с различными параметрами](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
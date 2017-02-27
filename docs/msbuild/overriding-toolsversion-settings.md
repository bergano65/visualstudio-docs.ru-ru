---
title: "Переопределение параметров ToolsVersion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, построение решений"
  - "MSBuild, переопределение параметра ToolsVersion"
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Переопределение параметров ToolsVersion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Набор инструментов для проектов и решений можно изменить одним из трех способов:  
  
1.  Используя переключатель `/ToolsVersion` \(или сокращенно `/tv`\) при сборке проекта или решения из командной строки  
  
2.  задавая параметр `ToolsVersion` задачи MSBuild  
  
3.  путем задания свойства `$(ProjectToolsVersion)` для проекта в решении.  Это позволяет собирать проект в решении с версией набора инструментов, отличающейся от используемой в других проектах.  
  
## Переопределение параметров ToolsVersion проектов и решений в сборках из командной строки  
 Хотя в проектах Visual Studio параметр ToolsVersion при сборке обычно задается в файле проекта, можно с помощью параметра командной строки `/ToolsVersion`  \(или `/tv`\) переопределить это значение и построить все проекты и зависимости между ними с использованием другого набора инструментов.  Например:  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 В этом примере построение всех проектов выполняется с использованием значения ToolsVersion 12.0. \(Тем не менее ознакомьтесь с подразделом "Очередность применения" далее в этом разделе.\)  
  
 Если в командной строке используется ключ `/tv`, можно в отдельных проектах использовать дополнительно свойство `$(ProjectToolsVersion)`, чтобы создать их с другим значением ToolsVersion по сравнению с остальными проектами в решении.  
  
## Переопределение значения ToolsVersion с использованием параметра ToolsVersion в задаче MSBuild  
 Задача MSBuild — основное средство для создания одного проекта из другого.  Чтобы в задаче MSBuild можно было создать проект со значением ToolsVersion, отличающимся от значения, заданного в проекте, предоставляется дополнительный параметр задачи с именем `ToolsVersion`.  В следующем примере демонстрируется применение этого параметра.  
  
1.  Создайте файл с именем `projectA.proj`, содержащий следующий код:  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go" >   
            <Message Text="projectA.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
  
            <MSBuild Projects="projectB.proj"  
                ToolsVersion="2.0"  
                Targets="go" />  
        </Target>  
    </Project>  
    ```  
  
2.  Создайте еще один файл с именем `projectB.proj`, содержащий следующий код:  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3.  В командной строке введите следующую команду:  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4.  Появится следующий вывод.  Для `projectA`, параметр `/toolsversion:3.5` в командной строке переопределяет параметр `ToolsVersion=12.0` в теге `Project`.  
  
     Метод `ProjectB` вызывается задачей в `projectA`.  Эта задача имеет `ToolsVersion=2.0`, которая переопределяет другие параметры `ToolsVersion` для `projectB`.  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## Очередность применения  
 В следующем списке показан порядок приоритетов от самого высокого до самого низкого:`ToolsVersion`  
  
1.  Атрибут `ToolsVersion` в задаче MSBuild, используемой для сборки проекта \(если имеется\).  
  
2.  Параметр `/toolsversion` \(или `/tv`\), которое используется в команде msbuild.exe, если таковые имеются.  
  
3.  Если переменная среды `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` задана, используйте текущую `ToolsVersion`.  
  
4.  Если переменная среды `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` задана и `ToolsVersion`, определенная в файле проекта, выше, чем текущая `ToolsVersion`, используйте текущую `ToolsVersion`.  
  
5.  Если переменная среды `MSBUILDLEGACYDEFAULTTOOLSVERSION` не задана или если `ToolsVersion` не задана, используются следующие действия:  
  
    1.  Атрибут `ToolsVersion` элемента [Project](../msbuild/project-element-msbuild.md) в файле проекта.  Если этот атрибут не существует, предполагается, что используется текущая версия.  
  
    2.  Версия набора инструментов, заданная по умолчанию в файле MSBuild.exe.config.  
  
    3.  Версия набора инструментов, заданная по умолчанию в реестре.  Для получения дополнительной информации см. [Стандартные и настраиваемые конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6.  Если переменная среды `MSBUILDLEGACYDEFAULTTOOLSVERSION` не задана, используются следующие действия:  
  
    1.  Если переменная среды `MSBUILDDEFAULTTOOLSVERSION` задана равной существующей `ToolsVersion`, используйте ее.  
  
    2.  Если свойство `DefaultOverrideToolsVersion` задано в MSBuild.exe.config, используйте его.  
  
    3.  Если `DefaultOverrideToolsVersion` задана в реестре, используйте ее.  
  
    4.  В противном случае используйте текущую `ToolsVersion`.  
  
## См. также  
 [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)   
 [Основные возможности MSBuild](../msbuild/msbuild-concepts.md)   
 [Набор инструментов \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Стандартные и настраиваемые конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md)
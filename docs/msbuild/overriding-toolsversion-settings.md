---
title: "Переопределение параметров ToolsVersion | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 24
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: ffb0544e0f48f0bd52ac3edb3a820b594d9d2264
ms.contentlocale: ru-ru
ms.lasthandoff: 05/13/2017

---
# <a name="overriding-toolsversion-settings"></a>Переопределение параметров ToolsVersion
Набор инструментов для проектов и решений можно изменить одним из трех способов.  
  
1.  Используя переключатель `/ToolsVersion` (или сокращенно `/tv`) при сборке проекта или решения из командной строки  
  
2.  Задав параметр `ToolsVersion` задачи MSBuild  
  
3.  Задав свойство `$(ProjectToolsVersion)` для проекта в решении. Это позволяет собирать проект в решении с версией набора инструментов, отличающейся от используемой в других проектах.  
  
## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Переопределение параметров ToolsVersion проектов и решений в сборках из командной строки  
 Хотя в проектах Visual Studio параметр ToolsVersion при сборке обычно задается в файле проекта, можно с помощью параметра командной строки `/ToolsVersion` (или `/tv`) переопределить это значение и построить все проекты и зависимости между ними с использованием другого набора инструментов. Пример:  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 В этом примере построение всех проектов выполняется с использованием значения ToolsVersion 12.0. (Тем не менее ознакомьтесь с подразделом "Очередность применения" далее в этом разделе.)  
  
 Если в командной строке используется параметр `/tv`, можно в отдельных проектах использовать дополнительно свойство `$(ProjectToolsVersion)`, чтобы создать их с другим значением ToolsVersion по сравнению с остальными проектами в решении.  
  
## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>Переопределение значения ToolsVersion с использованием параметра ToolsVersion в задаче MSBuild  
 Задача MSBuild — основное средство для создания одного проекта из другого. Чтобы в задаче MSBuild можно было создать проект со значением ToolsVersion, отличающимся от значения, заданного в проекте, предоставляется дополнительный параметр задачи с именем `ToolsVersion`. В следующем примере демонстрируется применение этого параметра.  
  
1.  Создайте файл с именем `projectA.proj`, содержащий следующий код.  
  
    ```xml  
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
  
2.  Создайте еще один файл с именем `projectB.proj`, содержащий следующий код.  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3.  В командной строке введите следующую команду.  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4.  Появится следующий результат. Для `projectA` параметр `/toolsversion:3.5` в командной строке переопределяет параметр `ToolsVersion=12.0` в теге `Project`.  
  
     Метод `ProjectB` вызывается задачей в `projectA`. Эта задача имеет параметр `ToolsVersion=2.0`, который переопределяет другие параметры `ToolsVersion` для `projectB`.  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## <a name="order-of-precedence"></a>Очередность применения  
 В следующем списке показан порядок приоритетов от самого высокого до самого низкого: `ToolsVersion`  
  
1.  Атрибут `ToolsVersion` в задаче MSBuild, используемой для сборки проекта (если имеется).  
  
2.  Параметр `/toolsversion` (или `/tv`), который используется в команде msbuild.exe, если таковой имеется.  
  
3.  Если задана переменная среды `MSBUILDTREATALLTOOLSVERSIONSASCURRENT`, используйте текущий параметр `ToolsVersion`.  
  
4.  Если задана переменная среды `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` и в файле проекта определен параметр `ToolsVersion` больший, чем текущий параметр `ToolsVersion`, используйте текущий параметр `ToolsVersion`.  
  
5.  Если задана переменная среды `MSBUILDLEGACYDEFAULTTOOLSVERSION` или если не задан параметр `ToolsVersion`, используются следующие действия.  
  
    1.  Атрибут `ToolsVersion` элемента [Project](../msbuild/project-element-msbuild.md) в файле проекта. Если этот атрибут не существует, предполагается, что используется текущая версия.  
  
    2.  Версия набора инструментов, заданная по умолчанию в файле MSBuild.exe.config.  
  
    3.  Версия набора инструментов, заданная по умолчанию в реестре. Дополнительные сведения см. в разделе [Стандартные и настраиваемые конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6.  Если переменная среды `MSBUILDLEGACYDEFAULTTOOLSVERSION` не задана, используются следующие действия.  
  
    1.  Если переменная среды `MSBUILDDEFAULTTOOLSVERSION` задана равной существующему параметру `ToolsVersion`, используйте ее.  
  
    2.  Если в MSBuild.exe.config задано свойство `DefaultOverrideToolsVersion` задано , используйте его.  
  
    3.  Если в реестре задано свойство `DefaultOverrideToolsVersion`, используйте его.  
  
    4.  В противном случае используйте текущий параметр `ToolsVersion`.  
  
## <a name="see-also"></a>См. также  
 [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)   
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [Набор инструментов (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Стандартные и настраиваемые конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md)

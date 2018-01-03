---
title: "Стандартные и настраиваемые конфигурации наборов инструментов | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: "31"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8f45cf4e58da23ffc0f0470f9d47658e75723552
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="standard-and-custom-toolset-configurations"></a>Стандартные и настраиваемые конфигурации наборов инструментов
Набор инструментов MSBuild содержит ссылки на задачи, целевые объекты и средства, которые можно использовать для создания проекта приложения. В состав MSBuild входит стандартный набор инструментов, но вы также можете создавать пользовательские наборы. Сведения об указании набора инструментов см. в разделе [Набор инструментов (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## <a name="standard-toolset-configurations"></a>Стандартные конфигурации набора инструментов  
 В MSBuild 12.0 входят следующие стандартные наборы инструментов:  
  
|ToolsVersion|Путь к набору инструментов (указанный в свойстве сборки MSBuildToolsPath или MSBuildBinPath)|  
|------------------|--------------------------------------------------------------------------------------------|  
|2.0|*Путь установки Windows*\Microsoft.Net\Framework\v2.0.50727\|  
|3.5|*Путь установки Windows*\Microsoft.NET\Framework\v3.5\|  
|4.0|*Путь установки Windows*\Microsoft.NET\Framework\v4.0.30319\|  
|12.0|*%ProgramFiles%*\MSBuild\12.0\bin|  
  
 Значение `ToolsVersion` определяет набор инструментов, который используется проектом, создаваемым в среде Visual Studio. В [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] значение по умолчанию — 12.0 (вне зависимости от версии, указанной в файле проекта), но этот атрибут можно переопределить с помощью параметра командной строки **/toolsversion**. Сведения об этом атрибуте и других способах указания `ToolsVersion` см. в разделе [Переопределение параметров ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 Если атрибут `ToolsVersion` не указан, в разделе реестра **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\\<Version Number\>\DefaultToolsVersion** определяется значение `ToolsVersion`, которое всегда равно 2.0.  
  
 Путь установки MSBuild.exe указывается в приведенных ниже разделах реестра.  
  
|Раздел реестра .|Имя ключа|Строковое значение параметра|  
|------------------|--------------|----------------------|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\2.0\|MSBuildToolsPath|Путь установки .NET Framework 2.0|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\|MSBuildToolsPath|Путь установки .NET Framework 3.5|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\|MSBuildToolsPath|Путь установки .NET Framework 4|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\12.0\|MSBuildToolsPath|Путь установки MSBuild|  
  
### <a name="sub-toolsets"></a>Поднаборы инструментов  
 Если раздел реестра в приведенной выше таблице содержит подраздел, MSBuild использует его для определения пути к вложенному набору инструментов, который может переопределять путь в родительском наборе инструментов. Вот пример такого подраздела:  
  
 \HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  
  
 Если какие-либо свойства определены как в базовом наборе инструментов, так и в выбранном вложенном, используются определения свойств из базового набора. Например, в наборе инструментов MSBuild 4.0 свойство `SDK40ToolsPath` указывает на SDK 7.0A, но в наборе инструментов MSBuild 4.0\11.0 это же свойство указывает на SDK 8.0A. Если значение `VisualStudioVersion` не задано, свойство `SDK40ToolsPath` будет указывать на версию 7.0A, но если для `VisualStudioVersion` задано значение 11.0, это свойство будет указывать на версию 8.0A.  
  
 Свойство сборки `VisualStudioVersion` указывает, активируется ли вложенный набор инструментов. Например, значение `VisualStudioVersion`, равное 12.0, определяет вложенный набор инструментов MSBuild 12.0. Дополнительные сведения см. в разделе о вспомогательных наборах инструментов статьи [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) (Набор инструментов ToolsVersion).  
  
> [!NOTE]
>  Не рекомендуется изменять эти параметры без необходимости. Тем не менее можно добавлять собственные параметры и задавать действующие в пределах компьютера пользовательские определения для набора инструментов, как описывается в следующем разделе.  
  
## <a name="custom-toolset-definitions"></a>Пользовательские определения для набора инструментов  
 Если стандартный набор инструментов не удовлетворяет требованиям сборки, можно создать пользовательский набор инструментов. Например, возможен сценарий сборки в лабораторной среде, в которой для сборки проектов [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] должна быть отдельная система. С помощью пользовательского набора инструментов можно при создании проектов или запуске файла MSBuild.exe присваивать атрибуту `ToolsVersion` пользовательские значения. Это позволяет также использовать свойство `$(MSBuildToolsPath)` для импорта файлов TARGETS из данного каталога и определять пользовательские свойства набора инструментов для любых проектов, использующих этот набор.  
  
 Укажите пользовательский набор инструментов в файле конфигурации для MSBuild.exe (или для пользовательского средства, в котором размещается ядро MSBuild). Например, файл конфигурации для MSBuild.exe может включать в себя указанное ниже определение набора инструментов, если требуется переопределить поведение ToolsVersion 12.0.  
  
```xml  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  
  
 В файле конфигурации также должен быть определен раздел `<msbuildToolsets>`, как показано ниже.  
  
```xml  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  Для правильного считывания `<configSections>` должен быть первым подразделом в разделе `<configuration>`.  
  
 `ToolsetConfigurationSection` — это пользовательский раздел конфигурации, который может использовать любой узел MSBuild в качестве пользовательской конфигурации. Если используется пользовательский набор инструментов, то серверу ничего не нужно делать для инициализации ядра сборки, кроме предоставления записей для файла конфигурации. Определив записи в реестре, можно задать действующий в пределах компьютера набор инструментов, применимый к MSBuild.exe, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и всем узлам MSBuild.  
  
> [!NOTE]
>  Если в файле конфигурации заданы параметры для `ToolsVersion`, которые уже были определены в реестре, то эти два определения не объединяются. Определение в файле конфигурации имеет приоритет, поэтому параметры в реестре для этого значения `ToolsVersion` не учитываются.  
  
 Следующие свойства зависят от того значения `ToolsVersion`, которое используется в проектах:  
  
-   **$(MSBuildBinPath)** — значение `ToolsPath`, которое задается либо в реестре, либо в файле конфигурации, где определено значение `ToolsVersion`. Параметр `$(MSBuildToolsPath)` в реестре или в файле конфигурации задает местоположение основных задач и целевых объектов. В файле проекта это соответствует свойству $(MSBuildBinPath), а также свойству $(MSBuildToolsPath).  
  
-   `$(MSBuildToolsPath)` — это зарезервированное свойство, которое предоставляется свойством MSBuildToolsPath, заданным в файле конфигурации. (Это свойство заменяет собой `$(MSBuildBinPath)`. Однако для обеспечения совместимости используется `$(MSBuildBinPath)`.) В пользовательском наборе инструментов должно быть определено свойство `$(MSBuildToolsPath)` или `$(MSBuildBinPath)`, но не оба эти свойства, если только их значения не совпадают.  
  
 Вы можете также добавить в файл конфигурации пользовательские и зависящие от ToolsVersion свойства, используя тот же самый синтаксис, который применяется для добавления свойства MSBuildToolsPath. Такие пользовательские свойства будут доступны для файла проекта, если используется имя, совпадающее со значением, указанным в файле конфигурации. В файле конфигурации можно определять наборы инструментов, но не вложенные наборы инструментов.  
  
## <a name="see-also"></a>См. также  
 [Набор инструментов (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
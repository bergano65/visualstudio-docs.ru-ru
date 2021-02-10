---
title: Стандартные и настраиваемые конфигурации наборов инструментов | Документы Майкрософт
description: Узнайте о стандартном и настраиваемом наборе инструментов MSBuild, который содержит ссылки на задачи, целевые объекты и средства для создания проекта приложения.
ms.custom: SEO-VS-2020
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70b0d85ea161a3f938013c01702dd2ccce73a31d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956104"
---
# <a name="standard-and-custom-toolset-configurations"></a>Стандартные и настраиваемые конфигурации наборов инструментов

Набор инструментов MSBuild содержит ссылки на задачи, целевые объекты и средства, которые можно использовать для создания проекта приложения. В состав MSBuild входит стандартный набор инструментов, но вы также можете создавать пользовательские наборы. Сведения об указании набора инструментов см. в разделе [Набор инструментов (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).

## <a name="standard-toolset-configurations"></a>Стандартные конфигурации набора инструментов

::: moniker range=">=vs-2019"
 MSBuild 16.0 содержит следующие стандартные наборы инструментов:

|ToolsVersion|Путь к набору инструментов (указанный в свойстве сборки MSBuildToolsPath или MSBuildBinPath)|
|------------------| - |
|2.0|*\<Windows installation path>\Microsoft.Net\Framework\v2.0.50727\\*|
|3.5|*\<Windows installation path>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows installation path>\Microsoft.NET\Framework\v4.0.30319\\*|
|Текущие|*\<Visual Studio installation path>\MSBuild\Current\bin*|

 Значение `ToolsVersion` определяет набор инструментов, который используется проектом, создаваемым в среде Visual Studio. В Visual Studio 2019 значение по умолчанию — Current (вне зависимости от версии, указанной в файле проекта), но этот атрибут можно переопределить с помощью параметра командной строки **/toolsversion**. Сведения об этом атрибуте и других способах указания `ToolsVersion` см. в статье [Переопределение параметров ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 ::: moniker-end

::: moniker range="vs-2017"
 В MSBuild 15.0 входят следующие стандартные наборы инструментов:

|ToolsVersion|Путь к набору инструментов (указанный в свойстве сборки MSBuildToolsPath или MSBuildBinPath)|
|------------------| - |
|2.0|*\<Windows installation path>\Microsoft.Net\Framework\v2.0.50727\\*|
|3.5|*\<Windows installation path>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows installation path>\Microsoft.NET\Framework\v4.0.30319\\*|
|15.0|*\<Visual Studio installation path>\MSBuild\15.0\bin*|

 Значение `ToolsVersion` определяет набор инструментов, который используется проектом, создаваемым в среде Visual Studio. В Visual Studio 2017 значение по умолчанию — "15.0" (вне зависимости от версии, указанной в файле проекта), но этот атрибут можно переопределить с помощью параметра командной строки **/toolsversion**. Сведения об этом атрибуте и других способах указания `ToolsVersion` см. в статье [Переопределение параметров ToolsVersion](../msbuild/overriding-toolsversion-settings.md).
 ::: moniker-end

В Visual Studio 2017 и последующих версиях не используется раздел реестра для хранения пути к MSBuild. Для версий MSBuild, предшествующих 15.0, которые установлены с Visual Studio 2017, путь установки MSBuild.exe указывается в приведенных ниже разделах реестра.

|Раздел реестра|Имя раздела|Строковое значение раздела|
|------------------|--------------|----------------------|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\2.0\\** |**MSBuildToolsPath**|**Путь установки .NET Framework 2.0**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\\** |**MSBuildToolsPath**|**Путь установки .NET Framework 3.5**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\\** |**MSBuildToolsPath**|**Путь установки .NET Framework 4**|

### <a name="sub-toolsets"></a>Поднаборы инструментов

 Если раздел реестра в приведенной выше таблице содержит подраздел, MSBuild использует его для определения пути к вложенному набору инструментов, который переопределяет путь в родительском наборе инструментов. Вот пример такого подраздела:

 **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0**

 Если какие-либо свойства определены как в базовом наборе инструментов, так и в выбранном вложенном, используются определения свойств из вложенного набора. Например, в наборе инструментов MSBuild 4.0 свойство `SDK40ToolsPath` указывает на SDK 7.0A, но в наборе инструментов MSBuild 4.0\11.0 это же свойство указывает на SDK 8.0A. Если значение `VisualStudioVersion` не задано, свойство `SDK40ToolsPath` будет указывать на версию 7.0A, но если для `VisualStudioVersion` задано значение 11.0, это свойство будет указывать на версию 8.0A.

 Свойство сборки `VisualStudioVersion` указывает, активируется ли вложенный набор инструментов. Например, значение `VisualStudioVersion`, равное 12.0, определяет вложенный набор инструментов MSBuild 12.0. Дополнительные сведения см. в разделе о вспомогательных наборах инструментов статьи [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) (Набор инструментов ToolsVersion).

> [!NOTE]
> Не рекомендуется изменять эти параметры без необходимости. Тем не менее можно добавлять собственные параметры и задавать действующие в пределах компьютера пользовательские определения для набора инструментов, как описывается в следующем разделе.

## <a name="custom-toolset-definitions"></a>Пользовательские определения для набора инструментов

 Если стандартный набор инструментов не удовлетворяет требованиям сборки, можно создать пользовательский набор инструментов. Например, возможен сценарий сборки в лабораторной среде, в которой для сборки проектов C++ должна быть отдельная система. С помощью пользовательского набора инструментов при создании проектов или запуске файла *MSBuild.exe* можно присваивать атрибуту `ToolsVersion` пользовательские значения. Это позволяет также использовать свойство `$(MSBuildToolsPath)` для импорта файлов *TARGETS* из указанного каталога и определять пользовательские свойства набора инструментов для любых проектов, в которых используется этот набор.

 Укажите пользовательский набор инструментов в файле конфигурации для *MSBuild.exe* (или для пользовательского средства, в котором размещается обработчик MSBuild). Например, файл конфигурации для *MSBuild.exe* может включать в себя указанное ниже определение набора инструментов, если требуется определить набор инструментов *MyCustomToolset*.

```xml
<msbuildToolsets default="MyCustomToolset">
   <toolset toolsVersion="MyCustomToolset">
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
       Microsoft.Build, Version=15.1.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a"
   </section>
</configSections>
```

> [!NOTE]
> Для правильного считывания `<configSections>` должен быть первым подразделом в разделе `<configuration>`.

 `ToolsetConfigurationSection` — это пользовательский раздел конфигурации, который может использовать любой узел MSBuild в качестве пользовательской конфигурации. Если используется пользовательский набор инструментов, то серверу ничего не нужно делать для инициализации ядра сборки, кроме предоставления записей для файла конфигурации.

 Следующие свойства зависят от того значения `ToolsVersion`, которое используется в проектах:

- **$(MSBuildBinPath)**  — значение `ToolsPath`, которое задается либо в реестре, либо в файле конфигурации, где определено значение `ToolsVersion`. Параметр `$(MSBuildToolsPath)` в реестре или в файле конфигурации задает местоположение основных задач и целевых объектов. В файле проекта это соответствует свойству $(MSBuildBinPath), а также свойству $(MSBuildToolsPath).

- `$(MSBuildToolsPath)` — это зарезервированное свойство, которое предоставляется свойством MSBuildToolsPath, заданным в файле конфигурации. (Это свойство заменяет собой `$(MSBuildBinPath)`. Однако для обеспечения совместимости используется `$(MSBuildBinPath)`.) В пользовательском наборе инструментов должно быть определено свойство `$(MSBuildToolsPath)` или `$(MSBuildBinPath)`, но не оба эти свойства, если только их значения не совпадают.

  Вы можете также добавить в файл конфигурации пользовательские и зависящие от ToolsVersion свойства, используя тот же самый синтаксис, который применяется для добавления свойства MSBuildToolsPath. Такие пользовательские свойства будут доступны для файла проекта, если используется имя, совпадающее со значением, указанным в файле конфигурации. В файле конфигурации можно определять наборы инструментов, но не вложенные наборы инструментов.

## <a name="see-also"></a>См. также

- [Набор инструментов (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)

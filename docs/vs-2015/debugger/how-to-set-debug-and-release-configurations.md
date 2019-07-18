---
title: Практическое руководство. Настройка отладки и выпуска | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4984355c12a92529a943fe6778740ac2d7f522f8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703640"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Практическое руководство. Настройка отладки и выпуска
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Проекты Visual Studio имеют отдельные конфигурации выпуска и отладки для вашей программы. Как следует из самих названий, производится построение отладочной версии для отладки и версии выпуска для окончательного выпуска программы.  
  
 Отладочная конфигурация программы компилируется с полной символической отладочной информацией и без оптимизации. Оптимизация усложняет отладку, поскольку усложняется связь между исходным кодом и сгенерированными инструкциями.  
  
 Конфигурация выпуска для программы полностью оптимизируется и не содержит символической отладочной информации. Отладочная информация может быть создана в виде PDB-файлов, в зависимости от используемых параметров компилятора. Создание PDB–файлов может оказаться очень полезным, если позднее возникнет необходимость в отладке версии выпуска.  
  
 Дополнительные сведения о конфигурациях сборки см. в разделе [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).  
  
 Можно изменить конфигурацию сборки из **построения** меню на панели инструментов или на страницах свойств проекта. Страницы свойств проекта зависят от конкретного языка. Следующая процедура показывает, как изменить конфигурацию сборки из меню и на панели инструментов. Дополнительные сведения об изменении конфигурации сборки в проектах на разных языках см. в разделе «См. также» ниже.  
  
### <a name="to-change-the-build-configuration"></a>Изменение конфигурации сборки  
  
1. В меню Построение: щелкните **сборки / Configuration Manager**, а затем выберите **Отладка** или **выпуска**.  
  
2. На панели инструментов выберите либо **Отладка** или **выпуска** из **конфигураций решения** поле со списком.  
  
     ![Конфигурация построения панели инструментов](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Эта панель инструментов недоступна в выпусках Express. Можно использовать **собрать решение F6** и **начать отладку F5** пунктов меню для выбора конфигурации.  
  
## <a name="see-also"></a>См. также  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Параметры проекта для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md)   
 [Конфигурации отладки и выпуска проекта](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)

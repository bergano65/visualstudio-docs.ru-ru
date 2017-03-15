---
title: "Практическое руководство. Обновление проектов Visual C++ до Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "проекты [C++], обновление"
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Практическое руководство. Обновление проектов Visual C++ до Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При первом открытии проекта Visual C\+\+, созданного в более ранней версии Visual Studio, может потребоваться обновить проект. В сообщении спрашивается, требуется ли выполнить обновление до последней версии компилятора и библиотек Visual C\+\+. Варианты обновления зависят от версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], которая использовалась для создания проекта.  
  
 Можно использовать [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] для открытия, правки и сборки проектов [!INCLUDE[win8](../debugger/includes/win8_md.md)], созданных в [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], однако для создания нового проекта [!INCLUDE[win8](../debugger/includes/win8_md.md)] необходимо использовать [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. \(Чтобы создать проект [!INCLUDE[win81](../debugger/includes/win81_md.md)], необходимо использовать [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)].\)  
  
 Для создания проекта Windows 10 нужно воспользоваться [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)].  
  
 Если вы не получили запрос на обновление проекта, возможно, не нужно ничего предпринимать для обновления проекта. Для получения дополнительной информации см. [Перенос, миграция и обновление проектов Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
-   Если проект \(VCPROJ\-файл\) был создан в версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], более ранней, чем [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], необходимо обновить проект.  
  
-   Если проект \(VCXPROJ\-файл\) создан в [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] или [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], возможны два варианта.  
  
    -   Можно пропустить обновление.[!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] загружает проект, не внося никаких изменений, если имеется доступ к средствам Visual C\+\+ в [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] с пакетом обновления 1 \(SP1\), [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] или [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]. Доступ к указанным средствам можно предоставить, установив версию Visual Studio, в которой был создан проект, на той же машине, где установлена [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)]. Для получения дополнительной информации см. [Параллельная установка версий Visual Studio](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md).  
  
    -   Проект можно обновить, разрешив [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] внести изменения, описанные далее в этом разделе. Если в решении имеется более одного проекта Visual C\+\+, необходимо обновить все проекты.  
  
        > [!NOTE]
        >  Если отклонить обновление при получении первой подсказки, можно обновить проект позднее, выбрав **Обновить проект VC\+\+** в меню **Проект**. Если команда не отображается, то обновление не требуется.  
  
## Обновление проекта Visual C\+\+  
 Если разрешить [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] автоматически обновлять проект, вносятся следующие изменения:  
  
-   Меняет проект так, что в нем используются библиотеки и компилятор [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] \(PlatformToolset \= VisualStudio v140\).  
  
-   Для проектов [!INCLUDE[cppcli](../misc/includes/cppcli_md.md)] TargetFrameworkVersion заменяется на .NET Framework 4.5.2.  
  
## Продолжение работы с пользовательским набором PlatformToolset  
 Если требуется работать с пользовательским набором PlatformToolset в [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)], набор инструментов должен находиться в папке %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ на компьютере x86 или в папке %ProgramFiles \(x86\)%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ на компьютере x64. Сведения о создании пользовательского набора PlatformToolset см. в разделе [Настройка для различных версий для C\+\+](http://go.microsoft.com/fwlink/?LinkId=248587) в блоге группы Visual C\+\+.  
  
## См. также  
 [Перенос, миграция и обновление проектов Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
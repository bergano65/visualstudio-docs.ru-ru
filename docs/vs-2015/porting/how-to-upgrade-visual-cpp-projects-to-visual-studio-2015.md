---
title: 'Практическое: обновление проектов Visual C++ для Visual Studio 2015 | Документация Майкрософт'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 047cb8733e1f1fa32e67b2fc7b6c53edb6174fcb
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54797056"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Практическое руководство. Обновление проектов Visual C++ до Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последние версии документации по Visual Studio 2017, см. в разделе [руководство по обновлению и переносу Visual C++](https://docs.microsoft.com/cpp/porting/visual-cpp-porting-and-upgrading-guide).

При первом открытии проекта Visual C++, созданного в более ранней версии Visual Studio, может потребоваться обновить проект. В сообщении спрашивается, требуется ли выполнить обновление до последней версии компилятора и библиотек Visual C++. Варианты обновления зависят от версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , которая использовалась для создания проекта.

 Можно использовать [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] для открытия, правки и сборки проектов [!INCLUDE[win8](../includes/win8-md.md)] , созданных в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], однако для создания нового проекта [!INCLUDE[win8](../includes/win8-md.md)] необходимо использовать [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. (Чтобы создать проект [!INCLUDE[win81](../includes/win81-md.md)] , необходимо использовать [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].)

 Для создания проекта Windows 10 нужно воспользоваться [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)].

 Если вы не получили запрос на обновление проекта, возможно, не нужно ничего предпринимать для обновления проекта.

-   Если проект (VCPROJ-файл) был создан в версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , более ранней, чем [!INCLUDE[vs2010](../includes/vs2010-md.md)], необходимо обновить проект.

-   Если проект (VCXPROJ-файл) создан в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)],  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]или [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] , возможны два варианта.

    -   Можно пропустить обновление. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] загружает проект, не внося никаких изменений, если имеется доступ к средствам Visual C++ в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] с пакетом обновления 1 (SP1), [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] или [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. Доступ к указанным средствам можно предоставить, установив версию Visual Studio, в которой был создан проект, на той же машине, где установлена [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]. Для получения дополнительной информации см. [Installing Visual Studio Versions Side-by-Side](../install/install-visual-studio-versions-side-by-side.md).

    -   Проект можно обновить, разрешив [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] внести изменения, описанные далее в этом разделе. Если в решении имеется более одного проекта Visual C++, необходимо обновить все проекты.

        > [!NOTE]
        >  Если отклонить обновление при получении первой подсказки, можно обновить проект позднее, выбрав **Обновить проект VC++** в меню **Проект** . Если команда не отображается, то обновление не требуется.

## <a name="upgrading-a-visual-c-project"></a>Обновление проекта Visual C++
 Если разрешить [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] автоматически обновлять проект, вносятся следующие изменения:

-   Меняет проект так, что в нем используются библиотеки и компилятор [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] (PlatformToolset = VisualStudio v140).

-   Для проектов [!INCLUDE[cppcli](../includes/cppcli-md.md)] TargetFrameworkVersion заменяется на .NET Framework 4.5.2.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Продолжение работы с пользовательским набором PlatformToolset
 Если требуется работать с пользовательским набором PlatformToolset в [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)], набор инструментов должен находиться в папке %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ на компьютере x86 или в папке %ProgramFiles (x86)%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ на компьютере x64. Сведения о создании пользовательского набора PlatformToolset см. в разделе [Настройка для различных версий для C++](http://go.microsoft.com/fwlink/?LinkId=248587) в блоге группы Visual C++.

## <a name="see-also"></a>См. также раздел
 [Visual C++, перенос и обновление руководство](http://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb) [перенос, миграция и обновление проектов Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)

---
title: 'Как: Установка визуализатора Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 499d644cc8374b070cedaf058b0e4dc17d155bdc
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880264"
---
# <a name="how-to-install-a-visualizer"></a>Практическое руководство. Установка визуализатора
После создания визуализатора необходимо установить его так, чтобы он стал доступен в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Установка визуализатора — это простой процесс.

> [!NOTE]
> В приложениях UWP поддерживаются только стандартные текстовые, HTML, XML и jSON-визуализаторы. Пользовательские визуализаторы (то есть, созданные пользователем) не поддерживаются.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Установка визуализатора для Visual Studio 2019
  
1. Найдите DLL, содержащий созданный вами визуализатор.

   Как правило, лучше всего, если как отладчик стороне DLL и отладки стороне DLL указать **любой процессор** в качестве целевой платформы. DLL стороны отладчика должен быть либо **любой процессор** или **32-битный**. Целевая платформа для отладочного DLL должна соответствовать процессу debugee.

2. Копируйте [DLL Debugger Side](create-custom-visualizers-of-data.md#to-create-the-debugger-side) DLL (и любые DLLs, от них зависит) в любое из следующих мест:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Копируйте [DLL Debuggee Side](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) DLL в любом из следующих мест:

    - *Рамочная программа* *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\`

    - `My Documents\`*Рамки* *VisualStudioVersion* `\Visualizers\`

    где *рамки* либо:
    - `net2.0`для отладчий, `.NET Framework` запустив время выполнения.
    - `netstandard2.0`для отладчий с помощью `netstandard 2.0` `.NET Framework v4.6.1+` времени `.NET Core 2.0+`выполнения, которое поддерживает (или ).
    - `netcoreapp`для отладчий, `.NET Core` запустив время выполнения. (поддерживает) `.NET Core 2.0+`

4. Перезапустите сеанс отладки.

> [!NOTE]
> Процедура отличается в Visual Studio 2017 и старше. Смотрите [предыдущую версию](how-to-install-a-visualizer.md?view=vs-2017) этой статьи.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Установка визуализатора для Visual Studio 2017 и старше

> [!IMPORTANT]
> Только визуализаторы .NET Framework поддерживаются в Visual Studio 2017 и старше.

1. Найдите библиотеку DLL, содержащую построенный визуализатор.

2. Скопируйте библиотеку DLL в одно из следующих мест:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Перезапустите сеанс отладки.

> [!NOTE]
> Если нужно использовать визуализатор управляемого кода для удаленной отладки, скопируйте DLL по тому же пути на удаленном компьютере.
::: moniker-end

## <a name="see-also"></a>См. также
- [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)
- [Практическое руководство. Написание визуализатора](create-custom-visualizers-of-data.md)

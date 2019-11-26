---
title: 'How to: Install a Visualizer | Microsoft Docs'
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
ms.openlocfilehash: 1df72c6978f5ab34a86c74dbc1ea349db5aa4457
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491304"
---
# <a name="how-to-install-a-visualizer"></a>Практическое руководство. Установка визуализатора
После создания визуализатора необходимо установить его так, чтобы он стал доступен в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Установка визуализатора — это простой процесс.

> [!NOTE]
> In UWP apps, only the standard text, HTML, XML, and JSON visualizers are supported. Пользовательские визуализаторы (то есть, созданные пользователем) не поддерживаются.

### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>To install a visualizer for Visual Studio 2019
  
1. Найдите библиотеку DLL, содержащую построенный визуализатор.

2. Copy the [Debugger Side](create-custom-visualizers-of-data.md#to-create-the-debugger-side) DLL to either of the following locations:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Copy the [Debuggee Side](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) DLL to either of the following locations:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    Where *Framework* is either:
    - `net2.0` for debuggees running the `.NET Framework` runtime.
    - `netstandard2.0` for debuggees using a runtime that supports `netstandard 2.0` (`.NET Framework v4.6.1+` or `.NET Core 2.0+`).
    - `netcoreapp` for debuggees running the `.NET Core` runtime. (supports `.NET Core 2.0+`)

4. Перезапустите сеанс отладки.

### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>To install a visualizer for Visual Studio 2017 and older

> [!IMPORTANT]
> Only .NET Framework visualizers are supported in Visual Studio 2017 and older

1. Найдите библиотеку DLL, содержащую построенный визуализатор.

2. Скопируйте библиотеку DLL в одно из следующих мест:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Перезапустите сеанс отладки.

> [!NOTE]
> Если нужно использовать визуализатор управляемого кода для удаленной отладки, скопируйте DLL по тому же пути на удаленном компьютере.

## <a name="see-also"></a>См. также
- [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)
- [Практическое руководство. Написание визуализатора](create-custom-visualizers-of-data.md)

---
title: Руководство. Установка визуализатора | Документация Майкрософт
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
ms.openlocfilehash: 2b7dfd28d70b80fd2d0f854b7db3550862b32814
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404372"
---
# <a name="how-to-install-a-visualizer"></a>Практическое руководство. Установка визуализатора
После создания визуализатора необходимо установить его так, чтобы он стал доступен в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Установка визуализатора — это простой процесс.

> [!NOTE]
> В приложениях UWP поддерживаются только стандартные визуализаторы Text, HTML, XML и JSON. Пользовательские визуализаторы (то есть, созданные пользователем) не поддерживаются.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Установка визуализатора для Visual Studio 2019
  
1. Откройте библиотеку DLL, содержащую созданный визуализатор.

2. Скопируйте библиотеку DLL на [стороне отладчика](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (и все библиотеки DLL, от которых она зависит) в одно из следующих расположений:

    - *Висуалстудиоинсталлпас* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Скопируйте библиотеку DLL [отлаживаемого](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) объекта в любое из следующих расположений:

    - *Висуалстудиоинсталлпас* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    где *платформа* является одной из следующих:
    - `net2.0` для дебугжеес, на котором запущена среда выполнения `.NET Framework`.
    - `netstandard2.0` для дебугжеес с использованием среды выполнения, поддерживающей `netstandard 2.0` (`.NET Framework v4.6.1+` или `.NET Core 2.0+`).
    - `netcoreapp` для дебугжеес, на котором запущена среда выполнения `.NET Core`. (поддерживает `.NET Core 2.0+`)

4. Перезапустите сеанс отладки.

> [!NOTE]
> Процедура отличается в Visual Studio 2017 и более ранних версиях. См. [предыдущую версию](how-to-install-a-visualizer.md?view=vs-2017) этой статьи.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Установка визуализатора для Visual Studio 2017 и более ранних версий

> [!IMPORTANT]
> В Visual Studio 2017 и более ранних версиях поддерживаются только визуализаторы .NET Framework.

1. Найдите библиотеку DLL, содержащую построенный визуализатор.

2. Скопируйте библиотеку DLL в одно из следующих мест:

    - *Висуалстудиоинсталлпас* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Перезапустите сеанс отладки.

> [!NOTE]
> Если нужно использовать визуализатор управляемого кода для удаленной отладки, скопируйте DLL по тому же пути на удаленном компьютере.
::: moniker-end

## <a name="see-also"></a>См. также:
- [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)
- [Практическое руководство. Написание визуализатора](create-custom-visualizers-of-data.md)

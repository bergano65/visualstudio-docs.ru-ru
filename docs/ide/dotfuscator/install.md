---
title: Установка Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: how-to
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2017, Visual Studio 2019, Visual Studio, install
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Узнайте, как установить бесплатную копию компонента Dotfuscator Community, входящую в состав Visual Studio.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 9f4ca634aa226437b6d8790837c9f95f778a00c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924769"
---
# <a name="install-dotfuscator-community"></a>Установка Dotfuscator Community

Dotfuscator Community является дополнительным компонентом Visual Studio.
В этих инструкциях объясняется, как его установить.

> [!NOTE]
> Помимо версий Dotfuscator Community, поставляемых с выпусками Visual Studio, PreEmptive Solutions периодически предоставляет обновленные версии на своем веб-сайте.
> Чтобы скачать **последнюю версию** напрямую, а не из установки Visual Studio, **[щелкните здесь, чтобы перейти на страницу скачиваемых файлов Dotfuscator][download]** .

## <a name="within-visual-studio"></a>В среде Visual Studio

::: moniker range="vs-2019"

Dotfuscator Community можно установить из интегрированной среды разработки Visual Studio:

1. В **поле поиска** (CTRL+Q) введите `dotfuscator`. <br/> <br/> ![Поле поиска](media/install_in_vs19_12.png) <br/> <br/>

2. В разделе *Компоненты* в результатах поиска установите флажок **Install PreEmptive Protection — Dotfuscator** (Установить PreEmptive Protection — Dotfuscator).
   * Если вы вместо этого в разделе *Меню* видите **PreEmptive Protection — Dotfuscator Community**, то Dotfuscator Community уже установлен. Чтобы [приступить к работе][get-started], выберите этот параметр.

3. Откроется окно установщика Visual Studio, автоматически настроенного для установки Dotfuscator Community.
   > [!NOTE]
   > Чтобы продолжить, может потребоваться указать учетные данные администратора.

4. В окне установщика Visual Studio щелкните *Установить*. <br/> <br/> ![Нажмите кнопку "Установить"](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

Dotfuscator Community можно установить из интегрированной среды разработки Visual Studio:

1. В панели поиска **Быстрый запуск** (CTRL+Q) введите `dotfuscator`. <br/> <br/> ![Быстрый запуск](media/install_from_vs_12.png) <br/> <br/>

2. Результаты появятся на панели быстрого запуска. В разделе *Установка* установите флажок **PreEmptive Protection — Dotfuscator (отдельный компонент)** .
   * Если вы вместо этого в разделе *Меню* видите **Сервис > PreEmptive Protection — Dotfuscator**, то Dotfuscator CE уже установлен. Чтобы [приступить к работе][get-started], выберите этот параметр.

3. Откроется окно установщика Visual Studio, автоматически настроенного для установки Dotfuscator CE.
   > [!NOTE]
   > Чтобы продолжить, может потребоваться указать учетные данные администратора.

4. В окне установщика Visual Studio щелкните *Установить*. <br/> <br/> ![Нажмите кнопку "Установить"](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

После завершения установки можно [начать использование Dotfuscator Community][get-started].

## <a name="during-visual-studio-installation"></a>Во время установки Visual Studio

Если вы еще не установили Visual Studio, можно получить установщик на [веб-сайте Visual Studio][vs-install].
При запуске он будет отображать варианты установки для выбранного выпуска Visual Studio.

::: moniker range="vs-2019"

![Параметры установки](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![Параметры установки](media/install_ui_17.png)

::: moniker-end

Затем можно установить Dotfuscator Community в качестве отдельного компонента Visual Studio.

1. Откройте вкладку **Отдельные компоненты**.
2. В разделе *Работа с кодом* выберите элемент *PreEmptive Protection — Dotfuscator*.<br/> <br/> ![Отдельные компоненты](media/install_individually_12.png) <br/> <br/>
3. На панели *Сводка* появится *PreEmptive Protection — Dotfuscator* в разделе *Отдельные компоненты*. <br/> <br/> ![Панель итогов](media/install_individually_3.png) <br/> <br/>
4. Настройте другие параметры установки, соответствующие вашей среде.
5. Когда все будет готово для установки Visual Studio, нажмите кнопку *Установить*.

После завершения установки можно начать использование Dotfuscator Community. Дополнительные сведения см. на [странице с инструкциями по началу работы в полном руководстве пользователя Dotfuscator Community][get-started].

## <a name="see-also"></a>См. также

[Этот раздел в полном руководстве пользователя Dotfuscator Community](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html

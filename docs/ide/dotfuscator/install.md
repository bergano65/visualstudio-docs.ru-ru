---
title: "Установка Dotfuscator Community Edition (CE) | Документы Майкрософт"
ms.date: 2017-06-22
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, защита, бесплатный выпуск, обфускация, .NET, бесплатно, Visual Studio 2017, установка"
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: "Узнайте, как установить бесплатный выпуск Dotfuscator Community Edition, входящий в состав Visual Studio 2017."
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: Joe-Sewell-PreEmptive
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
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: fb5356632ecf8183945b1d50ba940ed05abcf96f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/23/2017

---

# <a name="install-dotfuscator-community-edition-ce"></a>Установка Dotfuscator Community Edition (CE)

В Visual Studio 2017 представлена новая возможность установки с минимальным влиянием на работу системы.
Dotfuscator Community Edition (Dotfuscator CE) не устанавливается по умолчанию.
Однако процесс установки не вызывает трудностей, даже если вы уже установили Visual Studio.

> [!NOTE]
> Помимо версий Dotfuscator CE, поставляемых с выпусками Visual Studio, PreEmptive Solutions периодически предоставляет обновленные версии на своем веб-сайте.
> Чтобы скачать **последнюю версию** напрямую, а не из установки Visual Studio, **[щелкните здесь, чтобы перейти на страницу скачиваемых файлов Dotfuscator][download]**.

## <a name="within-visual-studio"></a>В среде Visual Studio

Dotfuscator CE можно установить из интегрированной среды разработки Visual Studio.

1. В панели поиска **Быстрый запуск** (CTRL+Q) введите `dotfuscator`. <br/> <br/> ![](media/install_from_vs_12.png) <br/> <br/>
2. Результаты появятся на панели быстрого запуска. В разделе *Установка* установите флажок **PreEmptive Protection — Dotfuscator (отдельный компонент)**.
  * Если вы вместо этого в разделе *Меню* видите **Сервис > PreEmptive Protection — Dotfuscator**, то Dotfuscator CE уже установлен. Дополнительные сведения об использовании см. на [странице с вводными сведениями полного руководства пользователя Dotfuscator CE][get-started].
3. Откроется окно установщика Visual Studio, автоматически настроенного для установки Dotfuscator CE.
  * Чтобы продолжить, может потребоваться указать учетные данные администратора.
4. Закройте все экземпляры интегрированной среды разработки Visual Studio. <br/> <br/> ![](media/install_from_vs_345.png) <br/> <br/>
5. В окне установщика Visual Studio щелкните *Установить*.

После завершения установки можно начать использование Dotfuscator CE. Дополнительные сведения см. на [странице с вводными сведениями полного руководства пользователя Dotfuscator CE][get-started].

## <a name="during-visual-studio-installation"></a>Во время установки Visual Studio

Если вы еще не установили Visual Studio 2017, можно получить установщик на [веб-сайте Visual Studio][2017-install].
При запуске он будет отображать варианты установки для выбранного выпуска Visual Studio.

![](media/install_ui.png)

Затем можно установить Dotfuscator CE в качестве отдельного компонента Visual Studio 2017.

1. Откройте вкладку **Отдельные компоненты**.
2. В разделе *Работа с кодом* выберите элемент *PreEmptive Protection — Dotfuscator*.<br/> <br/> ![](media/install_individually_12.png) <br/> <br/>
3. На панели *Сводка* появится *PreEmptive Protection — Dotfuscator* в разделе *Отдельные компоненты*. <br/> <br/> ![](media/install_individually_3.png) <br/> <br/>
4. Настройте другие параметры установки, соответствующие вашей среде.
5. Когда все будет готово для установки Visual Studio, нажмите кнопку *Установить*.

После завершения установки можно начать использование Dotfuscator CE. Дополнительные сведения см. на [странице с вводными сведениями полного руководства пользователя Dotfuscator CE][get-started].

## <a name="see-also"></a>См. также

[Этот раздел в полном руководстве пользователя Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[2017-install]: https://www.visualstudio.com/downloads/#vs-2017
[get-started]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]: https://www.preemptive.com/products/dotfuscator/downloads

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html


---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, Dotfuscator Community, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2019, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Узнайте, как защитить свои приложения .NET с помощью бесплатной копии средства Dotfuscator Community, включенного в Visual Studio 2017.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bf77f2796a224d6fad81c4a1485ba82f8822cfcc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557428"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

***PreEmptive Protection - Dotfuscator*** — это решение для комплексной защиты приложений .NET, которое легко встраивается в жизненный цикл разработки безопасного программного обеспечения.
Используйте его, чтобы обеспечить усиленную безопасность и настроить очистку рабочего стола, мобильных устройств, сервера и встроенных приложений. Так вы сможете защитить коммерческие тайны и другую интеллектуальную собственность от пиратства, подделки, изменения данных и несанкционированной отладки.
Решение Dotfuscator выполняется на скомпилированных сборках. Вам не нужно писать дополнительный код или иметь доступ к исходному коду.

![PreEmptive Protection — Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Почему важна защита

**Защищать интеллектуальную собственность** очень важно.
Код вашего приложения содержит сведения о проектировании и реализации, которые могут считаться интеллектуальной собственностью.
Приложения, созданные на платформе .NET Framework, [содержат важные метаданные и промежуточный код][assemblies]. Эту технологию легко изучить (декомпилировать) с помощью разных бесплатных автоматизированных средств.
Прервав и остановив такую декомпиляцию, вы сможет предотвратить несанкционированное раскрытие интеллектуальной собственности, а также продемонстрировать, что ваш код содержит коммерческую тайну.
Решение Dotfuscator позволяет выполнить [обфускацию][obfuscation] — маскировку или запутывание кода ваших сборок .NET, — чтобы помешать декомпиляции приложения, но сохранить его исходное поведение.

Также важно **обеспечить целостность приложения**.
Кроме декомпиляции, злоумышленники могут попытаться копировать ваши приложения, изменять поведение приложения в среде выполнения или манипулировать данными.
Dotfuscator позволяет внедрять в приложения функции, отвечающие за [выявление несанкционированного использования и реагирование на эти инциденты][checks] (сюда входит изменение данных, отладка, выполняемая сторонними лицами, и устройства с административным доступом).

Дополнительные сведения о том, как Dotfuscator встраивается в жизненный цикл безопасной разработки программного обеспечения, см. в описании решения PreEmptive на [странице, посвященной защите приложений SDL][sdl-protection].

## <a name="about-dotfuscator-community"></a>О Dotfuscator Community

Ваша копия Microsoft Visual Studio включает копию ***PreEmptive Protection — Dotfuscator Community***, доступную для бесплатного личного использования.
(Эта бесплатная версия ранее называлась Dotfuscator Community Edition или Dotfuscator CE.) См. инструкции по [установке версии Dotfuscator Community, входящей в состав Visual Studio][install].

Dotfuscator Community предлагает разработчикам, архитекторам и тест-инженерам ряд служб для обеспечения [защиты и безопасности программного обеспечения][software-protection].
Примеры [обфускации .NET][obfuscation] и других функций [защиты приложений][app-protection], включенных в Dotfuscator Community:

* *[Переименование][renaming]* идентификаторов затрудняет изучение технологии (декомпиляцию) скомпилированных сборок.
* *[Защита от незаконного изменения][tamper]* помогает выявлять выполнение незаконно измененных приложений, реагировать на незаконно измененные сеансы или прерывать их.
* *[Защита от отладки][debug]* позволяет обнаруживать в работающем приложении подключенный отладчик и прерывать сеансы отладки.
* *[Устройство с защитой от получения административного доступа][root]* используется для определения, работает ли приложение на устройстве Android с административным доступом, реагирования на сеансы на таких устройствах или их завершения.
* *[Поведение приложения после истечения срока действия][shelflife]* — позволяет закодировать дату истечения срока действия и прерывать сеансы приложения, срок действия которого истек.

Подробные сведения об этих возможностях и способах их включения в стратегию защиты приложения см. в статье о [возможностях Dotfuscator][capabilities].

Dotfuscator Community предоставляет настроенную систему базовой защиты.
Для зарегистрированных пользователей Dotfuscator Community и пользователей ***PreEmptive Protection — Dotfuscator Professional***, ведущего мирового решения по [обфускации .NET][net-obfuscator], доступны дополнительные способы защиты приложений.
Сведения о расширении Dotfuscator см. в статье, посвященной [обновлениям Dotfuscator Community Edition][upgrades].

## <a name="getting-started"></a>Начало работы

::: moniker range="vs-2019"

Чтобы начать использовать Dotfuscator Community в рамках Visual Studio, введите `dotfuscator` на **панели поиска** (CTRL+Q).

* Если вы уже установили Dotfuscator Community, в **поле поиска** под заголовком *Menus* (Меню) будет отображаться параметр, с помощью которого можно запустить Dotfuscator Community. Подробнее см. на [странице с инструкциями по началу работы в полном руководстве пользователя Dotfuscator Community][get-started].
* Если вы не установили Dotfuscator Community, в **поле поиска** вместо этого под заголовком *Individual Components* (Отдельные компоненты) будет отображаться параметр **Install PreEmptive Protection - Dotfuscator** (Установить PreEmptive Protection — Dotfuscator). Подробные сведения см. в статье об [установке Dotfuscator CE][install].

::: moniker-end

::: moniker range="vs-2017"

Чтобы начать использовать Dotfuscator Community в рамках Visual Studio, введите `dotfuscator` на **панели быстрого запуска** (CTRL+Q).

* Если вы установили Dotfuscator Community, при **быстром запуске** вы увидите *меню* для открытия пользовательского интерфейса Dotfuscator Community. Подробнее см. на [странице с инструкциями по началу работы в полном руководстве пользователя Dotfuscator Community][get-started].
* Если вы не установили Dotfuscator Community еще не установлено, при **быстром запуске** вам будет предложено выполнить *установку*. Подробные сведения см. в статье об [установке Dotfuscator CE][install].

::: moniker-end

Вы также можете скачать **последнюю версию** Dotfuscator Community на [странице preemptive.com][download].

## <a name="full-documentation"></a>Полная документация

Чтобы ознакомиться с возможностями Dotfuscator Community и воспользоваться [инструкциями по установке][install], перейдите по ссылке на соответствующую страницу со связанными ресурсами.

Подробнее о [работе с пользовательским интерфейсом Dotfuscator Community][get-started] см. в [полном руководстве пользователя Dotfuscator Community на сайте preemptive.com][full].

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html

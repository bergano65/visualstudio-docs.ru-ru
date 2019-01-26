---
title: Dotfuscator Community Edition (CE)
ms.date: 10/10/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, решения PreEmptive, защита PreEmptive, защита, community edition, обфускация, .NET, бесплатно, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Узнайте, как защитить свои приложения .NET с помощью бесплатного решения Dotfuscator Community Edition, включенного в Visual Studio 2017.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2760f56feabf5b5dfe90adf1b83856a456c9515d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987067"
---
# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE)

*PreEmptive Protection - Dotfuscator* — это решение для комплексной защиты приложений .NET, которое легко встраивается в жизненный цикл разработки безопасного программного обеспечения.
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

## <a name="about-dotfuscator-ce"></a>О программе Dotfuscator CE

Ваша копия Microsoft Visual Studio 2017 включает копию **_PreEmptive Protection - Dotfuscator_ Community Edition** (или Dotfuscator CE), доступную для бесплатного личного использования.
Инструкции по установке версии Dotfuscator CE, входящей в состав Visual Studio 2017, см. в статье [Install Dotfuscator Community Edition (CE)][install] (Установка Dotfuscator Community Edition).

Решение Dotfuscator CE предлагает разработчикам, архитекторам и тест-инженерам ряд служб для обеспечения [защиты и безопасности программного обеспечения][software-protection].
Далее описываются примеры [обфускации .NET][obfuscation] и других функций [защиты приложений][app-protection], включенных в Dotfuscator CE.

* *[Переименование][renaming]* идентификаторов затрудняет изучение технологии (декомпиляцию) скомпилированных сборок.
* *[Защита от незаконного изменения][tamper]* помогает выявлять выполнение незаконно измененных приложений, реагировать на незаконно измененные сеансы или прерывать их.
* *[Защита от отладки][debug]* позволяет обнаруживать в работающем приложении подключенный отладчик и прерывать сеансы отладки.
* *[Устройство с защитой от получения административного доступа][root]* используется для определения, работает ли приложение на устройстве Android с административным доступом, реагирования на сеансы на таких устройствах или их завершения.
* *[Поведение приложения после истечения срока действия][shelflife]* — позволяет закодировать дату истечения срока действия и прерывать сеансы приложения, срок действия которого истек.

Подробные сведения об этих возможностях и способах их включения в стратегию защиты приложения см. в статье о [возможностях Dotfuscator][capabilities].

Dotfuscator CE предоставляет готовую базовую защиту.
Для зарегистрированных пользователей Dotfuscator CE и пользователей *PreEmptive Protection — Dotfuscator*, ведущего мирового решения по [обфускации .NET][net-obfuscator], доступны дополнительные способы защиты приложений.
Сведения о расширении Dotfuscator см. в статье, посвященной [обновлениям Dotfuscator Community Edition][upgrades].

## <a name="getting-started"></a>Начало работы

Чтобы начать использовать решение Dotfuscator CE, включенное в Visual Studio, введите `dotfuscator` на панели поиска **быстрого запуска** (Ctrl+Q).

* Если решение Dotfuscator CE уже установлено, при **быстром запуске** вы увидите *меню* для пользовательского интерфейса Dotfuscator CE. Дополнительные сведения см. на [странице с вводными сведениями полного руководства пользователя Dotfuscator CE][get-started].
* Если решение Dotfuscator CE еще не установлено, при **быстром запуске** вам будет предложено *установить* его. Подробные сведения см. в статье об [установке Dotfuscator CE][install].

Вы также можете скачать **последнюю версию** Dotfuscator CE на [странице скачивания Dotfuscator preemptive.com][download].

## <a name="full-documentation"></a>Полная документация

Чтобы ознакомиться с возможностями Dotfuscator CE и воспользоваться [инструкциями по его установке][install], перейдите по ссылке на соответствующую страницу со связанными ресурсами.

Подробные инструкции по использованию решения, включая вводные сведения по [применению пользовательского интерфейса Dotfuscator CE][get-started], см. в [полном руководстве пользователя Dotfuscator CE на сайте preemptive.com][full].

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

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

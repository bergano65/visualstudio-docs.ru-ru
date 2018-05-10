---
title: Dotfuscator Community Edition (CE)
ms.date: 10/10/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
manager: douge
ms.openlocfilehash: c34eec9f8eab1f870344ec6995bfcbd8fea8739c
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
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
Решение Dotfuscator позволяет внедрять в приложения функции, отвечающие за [выявление несанкционированного использования, реагирование на эти инциденты и создание отчетов о них][checks] (сюда входит изменение данных, отладка, выполняемая посторонними лицами и устройства с административным доступом).

Дополнительные сведения о том, как Dotfuscator встраивается в жизненный цикл безопасной разработки программного обеспечения, см. в описании решения PreEmptive на [странице, посвященной защите приложений SDL][sdl-protection].

## <a name="about-dotfuscator-ce"></a>О программе Dotfuscator CE

Ваша копия Microsoft Visual Studio 2017 включает копию ***PreEmptive Protection - Dotfuscator* Community Edition** (или Dotfuscator CE), доступную для бесплатного личного использования.
Инструкции по установке версии Dotfuscator CE, входящей в состав Visual Studio 2017, см. в статье [Install Dotfuscator Community Edition (CE)][install] (Установка Dotfuscator Community Edition).

Решение Dotfuscator CE предлагает разработчикам, архитекторам и тест-инженерам ряд служб для обеспечения [защиты и безопасности программного обеспечения][software-protection].
Далее описываются примеры [обфускации .NET][obfuscation] и других функций [защиты приложений][app-protection], включенных в Dotfuscator CE.

* *[Переименование][renaming]* идентификаторов затрудняет изучение технологии (декомпиляцию) скомпилированных сборок.
* *[Защита от незаконного изменения][tamper]* помогает выявлять выполнение незаконно измененных приложений, передачу оповещений об инцидентах и прерывание измененных сеансов.
* *[Защита от отладки][debug]* для обнаружения вложения отладчика в работающее приложение, передачи оповещений об инцидентах и прерывания сеансов отладки.
* *[Устройство с защитой от получения административного доступа][root]* для определения того, что приложение выполняется на устройстве Android с административным доступом, и завершения сеансов на таких устройствах.
* *[Поведение истечения срока действия приложения][shelflife]* позволяет кодировать срок действия приложения, отправлять оповещения, если приложения выполняются после истечения срока действия, а также прерывать сеансы приложений с истекшим сроком действия.
* *[Отслеживание исключений][exceptions]* помогает отслеживать необработанные исключения в приложении.
* Отслеживание использования *[сеансов][sessions] и [функций ][features]*  помогает определить выполняемые версии и используемые функции приложений.

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

[assemblies]:  https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
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

[exceptions]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_exceptions.html
[sessions]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_sessions.html
[features]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_features.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
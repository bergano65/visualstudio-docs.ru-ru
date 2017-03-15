---
title: "Dotfuscator Community Edition (CE) | Документация Майкрософт"
ms.date: 2017-02-08
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, решения PreEmptive, защита PreEmptive, защита, community edition, обфускация, .NET, бесплатно, Visual Studio 2017"
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: "Узнайте, как защитить свои приложения .NET с помощью бесплатного решения Dotfuscator Community Edition, включенного в Visual Studio 2017."
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
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
translationtype: Human Translation
ms.sourcegitcommit: 507ff049dae50698d86e1536ed21ab982da1af85
ms.openlocfilehash: a4dd4e0f9a8f6c89452bc20e05139dfa5d062e0f
ms.lasthandoff: 02/22/2017

---

# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE)

*PreEmptive Protection – Dotfuscator* — это решение для комплексной защиты приложений .NET, которое легко встраивается в жизненный цикл разработки безопасного программного обеспечения. Используйте его, чтобы обеспечить усиленную безопасность и настроить очистку рабочего стола, мобильных устройств, сервера и встроенных приложений. Так вы сможете защитить коммерческие тайны и другую интеллектуальную собственность от пиратства, подделки, изменения данных и несанкционированной отладки.
Решение Dotfuscator выполняется на скомпилированных сборках. Вам не нужно писать дополнительный код или иметь доступ к исходному коду.

## <a name="why-protection-matters"></a>Почему важна защита

**Защищать интеллектуальную собственность** очень важно.
Код вашего приложения содержит сведения о проектировании и реализации, которые могут считаться интеллектуальной собственностью.
Приложения, созданные на платформе .NET Framework, [содержат важные метаданные и промежуточный код][assemblies]. Эту информацию легко проанализировать (декомпилировать) с помощью разных бесплатных автоматизированных средств.
Прервав и остановив такую декомпиляцию, вы сможет предотвратить несанкционированное раскрытие интеллектуальной собственности, а также продемонстрировать, что ваш код содержит коммерческую тайну.
Решение Dotfuscator позволяет выполнить [обфускацию][obfuscation] — маскировку или запутывание кода ваших сборок .NET, — чтобы помешать декомпиляции приложения, но сохранить его исходное поведение.

Также важно **обеспечить целостность приложения**.
Кроме декомпиляции, злоумышленники могут попытаться копировать ваши приложения, изменять поведение приложения в среде выполнения или манипулировать данными.
Решение Dotfuscator позволяет внедрять в приложения функции, отвечающие за [выявление несанкционированного использования, реагирование на эти инциденты и создание отчетов о них][checks] (сюда входит изменение данных и отладка, выполняемые посторонними лицами).

Дополнительные сведения о том, как Dotfuscator встраивается в жизненный цикл безопасной разработки программного обеспечения, см. в описании решения PreEmptive на [странице, посвященной защите приложений SDL][sdl-protection].

## <a name="about-dotfuscator-ce"></a>О программе Dotfuscator CE

Копия Microsoft Visual Studio 2017 включает бесплатную лицензию для ***PreEmptive Protection — Dotfuscator* Community Edition**, которая также называется Dotfuscator CE.
Инструкции по установке версии Dotfuscator CE, входящей в состав Visual Studio 2017, см. в статье [Install Dotfuscator Community Edition (CE)][install] (Установка Dotfuscator Community Edition).

Решение Dotfuscator CE предлагает разработчикам, архитекторам и инженерам-испытателям целый ряд служб для обеспечения [защиты и безопасности программного обеспечения][software-protection]. Далее описываются примеры [обфускации .NET][obfuscation] и других функций [защиты приложений][app-protection], включенных в Dotfuscator CE.

* *[Переименование][renaming]* идентификаторов затрудняет изучение технологии (декомпиляцию) скомпилированных сборок.
* *[Защита от незаконного изменения][tamper]* помогает выявлять выполнение незаконно измененных приложений, передачу оповещений об инцидентах и прерывание измененных сеансов.
* *[Защита от отладки][debug]* для обнаружения вложения отладчика в работающее приложение, передачи оповещений об инцидентах и прерывания сеансов отладки.
* *[Поведение истечения срока действия приложения][shelflife]* позволяет кодировать срок действия приложения, отправлять оповещения, если приложения выполняются после истечения срока действия, а также прерывать сеансы приложений с истекшим сроком действия.
* *[Отслеживание исключений][exceptions]* помогает отслеживать необработанные исключения в приложении.
* Отслеживание использования *[сеансов][sessions] и [функций ][features] * помогает определить выполняемые версии и используемые функции приложений.

Подробные сведения об этих возможностях и способах их включения в стратегию защиты приложения см. в статье о [возможностях Dotfuscator][capabilities].

Dotfuscator CE предоставляет готовую базовую защиту.
Для зарегистрированных пользователей Dotfuscator CE и пользователей *PreEmptive Protection — Dotfuscator*, ведущего мирового решения по [обфускации .NET][net-obfuscator], доступны дополнительные способы защиты приложений.
Сведения о расширении Dotfuscator см. в статье, посвященной [обновлениям Dotfuscator Community Edition][upgrades].

## <a name="getting-started"></a>Начало работы

Чтобы начать использовать решение Dotfuscator CE, включенное в Visual Studio, введите `dotfuscator` на панели поиска **быстрого запуска** (Ctrl+Q).

* Если решение Dotfuscator CE уже установлено, вы увидите *меню* для запуска пользовательского интерфейса Dotfuscator CE. Дополнительные сведения см. на [странице с вводными сведениями полного руководства пользователя Dotfuscator CE][get-started].
* Если решение Dotfuscator CE еще не установлено, вам будет предложено *установить* его. Подробные сведения см. в статье об [установке Dotfuscator CE][install].

Вы также можете скачать **последнюю версию** Dotfuscator CE на [странице скачивания Dotfuscator preemptive.com][download].

## <a name="full-documentation"></a>Полная документация

Чтобы ознакомиться с возможностями Dotfuscator CE и воспользоваться [инструкциями по установке средства][install], перейдите по ссылке на соответствующую страницу со связанными ресурсами.

Подробные инструкции по использованию решения, включая вводные сведения по [применению пользовательского интерфейса Dotfuscator CE][get-started], см. в [полном руководстве пользователя Dotfuscator CE на сайте preemptive.com][full].

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]: https://docs.microsoft.com/en-us/dotnet/articles/standard/assembly-format
[software-protection]: https://www.preemptive.com/software-protection
[obfuscation]: https://www.preemptive.com/obfuscation
[app-protection]: https://www.preemptive.com/application-protection
[sdl-protection]: https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[download]: https://www.preemptive.com/products/dotfuscator/downloads

[install]: install.md
[capabilities]: capabilities.md
[upgrades]: upgrades.md

[get-started]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/gui_getstarted.html

[renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/obfuscation_renaming.html

[checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_overview.html
[tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_tamper.html
[debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_debug.html
[shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_shelflife.html

[exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_exceptions.html
[sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_sessions.html
[features]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_features.html

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/index.html

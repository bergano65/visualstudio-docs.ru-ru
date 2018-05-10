---
title: Обновление Dotfuscator Community Edition (CE)
ms.date: 02/08/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, решения PreEmptive, защита PreEmptive, защита, community edition, обфускация, .NET, бесплатно, Visual Studio 2017, обновление, командная строка
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Узнайте, как обновить бесплатный выпуск Dotfuscator Community Edition, входящий в состав Visual Studio 2017.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: fcd5832b52c6cd9f72829c2bce8f7813b682cf4f
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="upgrade-dotfuscator-community-edition-ce"></a>Обновление Dotfuscator Community Edition (CE)

Dotfuscator Community Edition (Dotfuscator CE) предлагает множество функций защиты приложений, которые доступны всем разработчикам, использующим Microsoft Visual Studio.
Однако пользователям, обновившим версию Dotfuscator, доступны дополнительные функции.

## <a name="registering-dotfuscator-ce"></a>Регистрация Dotfuscator CE

Зарегистрированные пользователи Dotfuscator CE получают доступ к дополнительным функциям, таким как [поддержка командной строки][cli], позволяющим легко интегрировать Dotfuscator CE в ваш автоматический процесс сборки. Помимо этого, регистрация предоставляет доступ к Lucidator, встроенному средству, которое служит для [декодирования замаскированных трассировок стека][decode-obfuscated].

Регистрация производится быстро, просто и бесплатно.
Чтобы зарегистрировать Dotfuscator CE, см. [раздел "Регистрация Dotfuscator CE" на странице с вводными сведениями полного руководства пользователя Dotfuscator CE][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Хотя Dotfuscator Community Edition предоставляет базовый уровень защиты, **_PreEmptive Protection - Dotfuscator_ Professional Edition** включает улучшенные функции обфускации и возможности защиты. Улучшенные преобразования и возможности:

* *Защита интеллектуальной собственности*
  * Дополнительные возможности переименования, включая выбор случайного идентификатора и Enhanced Overload Induction™.
  * Инструментарий для декодирования замаскированных трассировок стека.
  * Доступ к преобразованиям обфускации корпоративного уровня, включая [преобразования, нацеленные на противодействие автоматической декомпиляции кода][control-flow].
  * Возможность [маскировать важные строки][string-encryption], делающая простой поиск декомпилированного кода невозможным.
  * Возможность [дискретно внедрять строки владения и распространения в ваши сборки][watermarking], что позволяет определить источник утечки информации, вызванной несанкционированным программным обеспечением.
  * Возможность [объединить несколько сборок в одну][linking], что еще больше затрудняет злоумышленникам задачу по определению ролей элементов кода, так как устраняется разделение областей ответственности.
  * Возможность [автоматически удалять неиспользуемый код из приложения][pruning], уменьшая объем важного кода, входящего в поставку.
* *Защита целостности приложений*
  * Дополнительные [меры для защиты приложений][check-actions].
  * Возможность выдачи предупреждений перед окончанием срока жизненного цикла приложения.
  * Возможность уведомить код приложения при приближении окончания жизненного цикла или после него.
  * Шифрование телеметрии.
* *Мониторинг приложений*
  * Возможность сбора и хранения сведений во время временных неполадок в сети.
  * Возможность сбора сведений частного характера.
  * Неограниченное использование [отслеживания функций][features].
  * Возможность отслеживания исключений, созданных и перехваченных в коде, в дополнение к необработанным исключениям.
  * Возможность отслеживания исключений в сборках `.dll`.
  * Шифрование телеметрии.

Dotfuscator Professional — это отраслевой стандарт [маскировщика .NET][net-obfuscator], подходящий для корпоративных разработчиков, которым нужны оперативные обновления, поддержка и обслуживание.
Кроме того, Dotfuscator Professional обеспечивает тесную интеграцию с Visual Studio и лицензируется для коммерческого использования.

Дополнительные сведения о расширенных функциях защиты приложений Dotfuscator Professional см. на [странице обзора Dotfuscator][product-about] PreEmptive Solutions и [сравните их с Community Edition][product-compare].
[Полностью поддерживаемые пробные версии доступны на сайте preemptive.com][eval].

## <a name="see-also"></a>См. также

[Эта статья в полном руководстве пользователя Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions
[features]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/instrumentation_features.html

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html
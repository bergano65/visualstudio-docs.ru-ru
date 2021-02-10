---
title: Обновление Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2019, Visual Studio 2017, Visual Studio, upgrade, command line
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
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
description: Узнайте, как обновить бесплатную копию компонента Dotfuscator Community, входящую в состав Visual Studio.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: a0e3ad3e5f6afbd6675f8e65c918b4a5d7c66dd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922780"
---
# <a name="upgrade-dotfuscator-community"></a>Обновление Dotfuscator Community

Dotfuscator Community предлагает множество функций защиты приложений, которые доступны всем разработчикам, использующим Microsoft Visual Studio.
Однако пользователям, обновившим версию Dotfuscator, доступны дополнительные функции.

## <a name="registering-dotfuscator-community"></a>Регистрация Dotfuscator Community

Зарегистрированные пользователи Dotfuscator Community получают доступ к дополнительным функциям, таким как [поддержка командной строки][cli], позволяющим легко интегрировать Dotfuscator Community в ваш автоматический процесс сборки. Помимо этого, регистрация предоставляет доступ к встроенному средству, которое служит для [декодирования замаскированных трассировок стека][decode-obfuscated].

Регистрация производится быстро, просто и бесплатно.
Чтобы зарегистрировать Dotfuscator Community, обратитесь к [инструкциям в полном руководстве пользователя Dotfuscator Community][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Хотя Dotfuscator Community предоставляет базовый уровень защиты, ***PreEmptive Protection — Dotfuscator Professional*** включает улучшенные функции обфускации и возможности защиты, например:

* *Защита интеллектуальной собственности*
  * Дополнительные возможности переименования, включая выбор случайного идентификатора и Enhanced Overload Induction™.
  * Доступ к преобразованиям обфускации корпоративного уровня, включая [преобразования, нацеленные на противодействие автоматической декомпиляции кода][control-flow].
  * Возможность [маскировать важные строки][string-encryption], делающая простой поиск декомпилированного кода невозможным.
  * Возможность [дискретно внедрять строки владения и распространения в ваши сборки][watermarking], что позволяет определить источник утечки информации, вызванной несанкционированным программным обеспечением.
  * Возможность [объединить несколько сборок в одну][linking], что еще больше затрудняет злоумышленникам задачу по определению ролей элементов кода, так как устраняется разделение областей ответственности.
  * Возможность [автоматически удалять неиспользуемый код из приложения][pruning], уменьшая объем важного кода, входящего в поставку.
* *Защита целостности приложений*
  * Дополнительные [меры для защиты приложений][check-actions].
  * Возможность выдачи предупреждений перед окончанием срока жизненного цикла приложения.
  * Возможность уведомить код приложения при приближении окончания жизненного цикла или после него.

Dotfuscator Professional — это отраслевой стандарт [маскировщика .NET][net-obfuscator], подходящий для корпоративных разработчиков, которым нужны оперативные обновления, поддержка и обслуживание.
Кроме того, Dotfuscator Professional обеспечивает тесную интеграцию с Visual Studio и лицензируется для коммерческого использования.

Дополнительные сведения о расширенных функциях защиты приложений Dotfuscator Professional см. на [странице обзора Dotfuscator][product-about] PreEmptive Solutions и [сравните их с Dotfuscator Community][product-compare].
[Полностью поддерживаемые пробные версии доступны на сайте preemptive.com][eval].

## <a name="see-also"></a>См. также раздел

[Эта статья в полном руководстве пользователя Dotfuscator Community][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html

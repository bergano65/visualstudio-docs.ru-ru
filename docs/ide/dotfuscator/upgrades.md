---
title: "Обновление Dotfuscator Community Edition (CE) | Документация Майкрософт"
ms.date: 2017-02-08
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, решения PreEmptive, защита PreEmptive, защита, community edition, обфускация, .NET, бесплатно, Visual Studio 2017, обновление, командная строка"
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
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
description: "Узнайте, как обновить бесплатный выпуск Dotfuscator Community Edition, входящий в состав Visual Studio 2017."
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
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
ms.openlocfilehash: eeabf6db465f57ab373c592b01a682ed6442800f
ms.lasthandoff: 02/22/2017

---

# <a name="upgrade-dotfuscator-community-edition-ce"></a>Обновление Dotfuscator Community Edition (CE)

Dotfuscator Community Edition (Dotfuscator CE) предлагает множество функций защиты приложений, которые доступны всем разработчикам, использующим Microsoft Visual Studio.
Однако пользователям, обновившим версию Dotfuscator, доступны дополнительные функции.

## <a name="registering-dotfuscator-ce"></a>Регистрация Dotfuscator CE

Зарегистрированные пользователи Dotfuscator CE получают доступ к дополнительным функциям, таким как [поддержка командной строки][cli], позволяющим легко интегрировать Dotfuscator CE в ваш автоматический процесс сборки.

Регистрация производится быстро, просто и бесплатно.
Чтобы зарегистрировать Dotfuscator CE, см. [раздел "Регистрация Dotfuscator CE" на странице с вводными сведениями полного руководства пользователя Dotfuscator CE][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Хотя Dotfuscator Community Edition предоставляет базовый уровень защиты, ***PreEmptive Protection - Dotfuscator* Professional Edition** включает улучшенные функции обфускации и возможности защиты.
Сюда входит следующее.

* *Защита интеллектуальной собственности*
  * Дополнительные возможности переименования, включая выбор случайного идентификатора и Enhanced Overload Induction™.
  * Инструментарий для декодирования замаскированных трассировок стека.
  * Доступ к преобразованиям обфускации корпоративного уровня, включая [преобразования, нацеленные на противодействие автоматической декомпиляции кода][control-flow].
  * Возможность [маскировать важные строки][string-encryption], делающая простой поиск декомпилированного кода невозможным.
  * Возможность [дискретно внедрять строки владения и распространения в ваши сборки][watermarking] (водяные знаки программного обеспечения), что позволяет определить источник несанкционированного программного обеспечения утечки.
  * Возможность [объединить несколько сборок в одну][linking], что еще больше затрудняет злоумышленникам задачу по определению ролей элементов кода, так как устраняется разделение областей ответственности.
  * Возможность [автоматически удалять неиспользуемый код из приложения][pruning], уменьшая объем важного кода, входящего в поставку.
* *Защита целостности приложений*
  * Дополнительные [меры для защиты приложений][check-actions].
  * Возможность внедрения кода для защиты от незаконного изменения и противодействия отладке в сборки `.dll`.
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
[Полностью поддерживаемые пробные версии доступны по запросу на сайте preemptive.com][eval].

## <a name="see-also"></a>См. также

[Этот раздел в полном руководстве пользователя Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]: https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]: https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]: https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]: https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]: https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Check%20Actions.html
[features]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Feature_Usage_Tracking_and_the_Feature_Attribute.html

[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[eval]: https://www.preemptive.com/eval-request

[product-about]: https://www.preemptive.com/products/dotfuscator/overview
[product-compare]: https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/intro_cli.html
[register-ce]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/gui_getstarted.html#register

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/intro_upgrades.html

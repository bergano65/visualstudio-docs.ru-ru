---
title: Возможности Dotfuscator
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2017, Visual Studio 2019, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Узнайте о возможностях бесплатной копии Dotfuscator Community, входящей в состав Visual Studio.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: ad53c99656096fec2393ecbd9f63fbffe1343e9a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924803"
---
# <a name="capabilities-of-dotfuscator"></a>Возможности Dotfuscator

Эта страница посвящена возможностям Dotfuscator Community, а также содержит несколько ссылок на дополнительные параметры, доступные посредством [обновлений][upgrades].

Dotfuscator Community — это система для приложений .NET, применяемая *после сборки*.
С помощью Dotfuscator CE пользователи Visual Studio могут [маскировать сборки][obfuscation], а также внедрять [активную защиту][checks] в приложение, при этом для Dotfuscator не требуется доступ к исходному коду.
Dotfuscator защищает приложение несколькими способами, создавая многоуровневую защиту.

Dotfuscator Community поддерживает обширный диапазон типов сборок и приложений .NET, включая [универсальную платформу Windows (UWP)][uwp] и [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Защита интеллектуальной собственности

Структура, поведение и реализация приложения являются формами интеллектуальной собственности (IP).
Однако приложения, созданные для платформы .NET, похожи на раскрытые книги; сборки .NET легко реконструировать, [так как они содержат высокоуровневые метаданные и промежуточный код][assemblies].

Dotfuscator Community включает базовые функции [обфускации .NET][obfuscation] в виде [переименования][renaming].
Обфускация кода с помощью Dotfuscator снижает риск несанкционированного доступа к исходному коду посредством реконструирования, в результате чего важные сведения об именах перестанут быть открытыми.
Обфускация кода также указывает на предпринимаемые пользователем усилия по защите кода от изучения, что является важным этапом при сохранении коммерческой тайны.

Многие [функции защиты целостности приложения](#application-integrity-protection) в Dotfuscator Community еще больше затрудняют реконструирование.
Например, недобросовестной субъект может попытаться подключить отладчик к запущенному экземпляру приложения, чтобы понять логику программы.
Чтобы воспрепятствовать этому, Dotfuscator позволяет внедрить в приложение [меры противодействия отладке][debug].

## <a name="application-integrity-protection"></a>Защита целостности приложений

Кроме защиты исходного кода также важно убедиться, что приложение используется, как и было задумано.
Злоумышленники могут пытаться перехватить приложение для обхода политик лицензирования (т. е. пиратства), кражи или изменения обрабатываемых приложением конфиденциальных данных либо для изменения поведения приложения.

Dotfuscator Community может внедрить [код проверки приложения][checks] в сборки, в том числе меры по [защите от незаконного изменения][tamper], [противодействию отладке][debug] и [защите от административного доступа][root].
При обнаружении недопустимого состояния приложения код проверки может [вызывать код приложения, чтобы разрешить ситуацию соответствующим образом][check-app].
Или, если вы не хотите писать код обработки недопустимых способов использования приложения, Dotfuscator позволяет внедрить поддержку [ответов][check-action] без изменений в исходном коде.

Многие из этих методов также подходят для обеспечения нужных [сроков действия][shelflife] для ознакомительных или пробных версий программного обеспечения.

## <a name="see-also"></a>См. также

[Этот раздел в полном руководстве пользователя Dotfuscator Community][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html

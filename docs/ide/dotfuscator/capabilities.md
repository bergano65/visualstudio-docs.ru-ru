---
title: Возможности Dotfuscator
ms.date: 10/10/2017
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, решения PreEmptive, защита PreEmptive, защита, community edition, обфускация, .NET, бесплатно, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Узнайте о возможностях бесплатного выпуска Dotfuscator Community Edition, входящего в состав Visual Studio 2017.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9182593e16be2a8e09331a49427623e5c81a9a9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55925362"
---
# <a name="capabilities-of-dotfuscator"></a>Возможности Dotfuscator

Эта страница посвящена возможностям Dotfuscator Community Edition (Dotfuscator CE), а также содержит несколько ссылок на дополнительные параметры, доступные посредством [обновлений][upgrades].

Dotfuscator — это система для приложений .NET, применяемая *после сборки*.
С помощью Dotfuscator CE пользователи Visual Studio могут [маскировать сборки][obfuscation], а также внедрять [активную защиту][checks] в приложение, при этом для Dotfuscator не требуется доступ к исходному коду.
Dotfuscator защищает приложение несколькими способами, создавая многоуровневую защиту.

Dotfuscator CE поддерживает обширный диапазон типов сборок и приложений .NET, включая [универсальную платформу Windows (UWP)][uwp] и [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Защита интеллектуальной собственности

Структура, поведение и реализация приложения являются формами интеллектуальной собственности (IP).
Однако приложения, созданные для платформы .NET Framework, похожи на раскрытые книги; сборки .NET очень легко реконструировать, [так как они содержат высокоуровневые метаданные и промежуточный код][assemblies].

Dotfuscator CE включает базовые функции [обфускации .NET][obfuscation] в виде [переименования][renaming].
Обфускация кода с помощью Dotfuscator снижает риск несанкционированного доступа к исходному коду посредством реконструирования, в результате чего важные сведения об именах перестанут быть открытыми.
Обфускация кода также указывает на предпринимаемые пользователем усилия по защите кода от изучения, что является важным этапом при сохранении коммерческой тайны.

Многие [функции защиты целостности приложения](#application-integrity-protection) в Dotfuscator CE еще больше затрудняют реконструирование.
Например, недобросовестной субъект может попытаться подключить отладчик к запущенному экземпляру приложения, чтобы понять логику программы.
Чтобы воспрепятствовать этому, Dotfuscator позволяет внедрить в приложение [меры противодействия отладке][debug].

## <a name="application-integrity-protection"></a>Защита целостности приложений

Кроме защиты исходного кода также важно убедиться, что приложение используется, как и было задумано.
Злоумышленники могут пытаться перехватить приложение для обхода политик лицензирования (т. е. пиратства), кражи или изменения обрабатываемых приложением конфиденциальных данных либо для изменения поведения приложения.

Dotfuscator CE может внедрить [код проверки приложения][checks] в сборки, в том числе меры по [защите от незаконного изменения][tamper], [противодействию отладке][debug] и [защите от административного доступа][root].
При обнаружении недопустимого состояния приложения код проверки может [вызывать код приложения, чтобы разрешить ситуацию соответствующим образом][check-app].
Или, если вы не хотите писать код обработки недопустимых способов использования приложения, Dotfuscator позволяет внедрить поддержку [ответов][check-action] без изменений в исходном коде.

Многие из этих методов также подходят для обеспечения нужных [сроков действия][shelflife] для ознакомительных или пробных версий программного обеспечения.

## <a name="see-also"></a>См. также раздел

[Этот раздел в полном руководстве пользователя Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
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

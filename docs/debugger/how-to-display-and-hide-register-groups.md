---
title: Как выполнить Отображение и скрытие групп регистров | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.registergroups
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, displaying and hiding register groups
- register groups, displaying and hiding
ms.assetid: 6be5dfb4-4cfe-4daf-b538-60405640857d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be702dcd19506e6da8fb1e291aa5262dbf4399b2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018453"
---
# <a name="how-to-display-and-hide-register-groups-c-c-visual-basic-f"></a>Как выполнить Отображение и скрытие групп регистров (C#, C++, Visual Basic, F#)

Окно **Регистры** доступно только при включении отладки на уровне адреса в категории **Общие** узла **Отладка** диалогового окна **Параметры**.

Чтобы избежать загромождения, в окне **Регистры**  регистры упорядочены по группам. Если щелкнуть правой кнопкой мыши в окне **Регистры**, появится контекстное меню, содержащее эти группы, и с помощью процедуры, описанной ниже, можно, по своему усмотрению, отобразить или скрыть эти группы.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

## <a name="display-or-hide-register-groups"></a>Отображение или скрытие групп регистров

1.  Щелкните правой кнопкой мыши окно **Регистры**.

2.  Выберите в контекстном меню группы регистров, которые нужно показать или скрыть.

     Группы регистров, не поддерживаемые оборудованием, на котором выполняется отладка, недоступны в контекстном меню, поэтому они не могут быть выбраны.

## <a name="see-also"></a>См. также

- [Практическое руководство. Использование окна регистров](../debugger/how-to-use-the-registers-window.md)
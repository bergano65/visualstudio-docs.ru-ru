---
title: Представление значения регистров в отладчике | Документация Майкрософт
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8622bb1288324429ad346834930559d1435ac6d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867583"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Представление значения регистров в окно "Регистры" (C#, C++, Visual Basic, F#)

**Регистрирует** окне отображается содержимое регистров во время отладки Visual Studio. Высокоуровневые введение в принципы использования регистров и **регистрирует** окно, см. в разделе [основы отладки: окно регистров](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Сведения о регистрах не доступно для скриптов и приложений SQL.

Во время отладки, зарегистрируйте изменении значений, так как выполняется код в приложении. Значения, которые были изменены, недавно отображаться красным цветом на **регистрирует** окна.

Для упорядочивания регистры в окне **Регистры** объединены в группы, которые зависят от платформы и типа процессора. Можно отобразить или скрыть группы регистров. Дополнительные сведения см. в разделе [Как отображать и скрывать группы регистров](../debugger/how-to-display-and-hide-register-groups.md).

Значения регистров можно изменять. Дополнительные сведения см. в разделе [Как изменить значение регистра](../debugger/how-to-edit-a-register-value.md).

**Чтобы открыть окно "Регистры"**

1. Включение отладки, выбрав **включить отладку на уровне адреса** в **средства** (или **Отладка**) > **параметры**  >  **Отладки**.

1. Во время отладки или выполнения в точке останова, выберите **Отладка** > **Windows** > **регистрирует**, или нажмите клавишу **Alt** + **5**.

>[!NOTE]
>Диалоговые окна и команды меню могут отличаться в зависимости от выпуска Visual Studio или параметры. Чтобы изменить параметры, выберите **Импорт и экспорт параметров** на Visual Studio **средства** меню. Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>См. также

- [Общие сведения об отладке: окно регистров](../debugger/debugging-basics-registers-window.md)
- [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)

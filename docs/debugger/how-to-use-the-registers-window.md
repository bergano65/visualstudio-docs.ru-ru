---
title: Просмотр значений регистров в отладчике | Документация Майкрософт
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: afcada407060af2072e3cf1c30e86153762890b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906005"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Просмотр значений регистров в окне "Регистры" (C#, C++, Visual Basic, F#)

Во время отладки Visual Studio в окне **Регистры** отображается содержимое регистров. Высокоуровневое введение в принципы использования регистров и **регистрирует** окно, см. в разделе [Основы отладки: Окно регистров](../debugger/debugging-basics-registers-window.md)

> [!NOTE]
> Для скриптов и приложений SQL сведения о регистрах недоступны.

Во время отладки, при выполнении кода в приложении, значения регистров меняются. Значения, которые недавно изменились, отображаются в окне **Регистры** красным цветом.

Для упорядочивания регистры в окне **Регистры** объединены в группы, которые зависят от платформы и типа процессора. Группы регистров можно отобразить или скрыть. Дополнительные сведения см. в разделе [Практическое руководство. отображать и скрывать группы регистров](../debugger/how-to-display-and-hide-register-groups.md).

Сведения о флагах, отображаемых в окне **Регистры**, см. в статье [Сведения об окне регистров](../debugger/debugging-basics-registers-window.md)

Значения регистров можно изменять. Дополнительные сведения см. в разделе [Практическое руководство. изменить значение регистра](../debugger/how-to-edit-a-register-value.md).

**Чтобы открыть окно регистров**

1. Включите отладку на уровне адреса, выбрав **Включить отладку на уровне адреса**в пункте **Средства** (или **Отладка**) > **Параметры** > **Отладка**.

1. Во время отладки или в точке останова выберите **Отладка** > **Windows** > **Регистр** или нажмите **Alt**+**5**.

>[!NOTE]
>Диалоговые окна и команды меню могут отличаться в зависимости от выпуска Visual Studio или параметров. Чтобы изменить параметры, выберите в меню **Сервис** Visual Studio пункт **Импорт и экспорт параметров**. Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>См. также

- [Общие сведения об отладке: окно регистров](../debugger/debugging-basics-registers-window.md)
- [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)

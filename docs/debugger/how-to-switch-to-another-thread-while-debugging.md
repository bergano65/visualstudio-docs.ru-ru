---
title: Переключение на другой поток при отладке
ms.custom: seodec18
ms.date: 04/27/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11ad6280ad1213008bbb8ca8f6311ca34231d308
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732445"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Практическое руководство. Переключение на другой поток при отладке в Visual Studio (C#, Visual Basic, C++)
При отладке многопоточных приложений существует несколько способов переключения с потока, над которым ведется работа, на другой поток.

> [!NOTE]
> Если вы хотите управлять порядком, в котором выполняются потоки, вам нужно [замораживать и размораживать потоки](../debugger/get-started-debugging-multithreaded-apps.md).

Когда вы исследуете потоки в редакторе кода и различных окнах многопоточной отладки, желтая стрелка указывает текущий поток. Зеленая стрелка с загнутым наконечником указывает, что поток, не являющийся текущим, имеет текущий контекст отладчика.

### <a name="to-switch-to-any-thread-that-appears"></a>Переключение на любой отображаемый поток

- В окне **Потоки** или **Контроль параллельных данных** дважды щелкните нужный поток.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Переключение на поток в окне исходного кода

- В поле слева щелкните правой кнопкой мыши значок метки потока ![Метка потока](../debugger/media/dbg-thread-marker.png "ThreadMarker"), выберите команду **Переключиться в**, а затем щелкните имя потока, в который хотите переключиться. В контекстном меню отображаются только потоки, работающие с этой конкретной точкой кода.

     Если никакие метки потока не отображаются, щелкните правой кнопкой мыши в окне **Потоки** и проверьте, установлен ли флажок **Показать потоки в исходном коде**.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Переключение на поток в панели инструментов "Место отладки"

1. В панели инструментов **Место отладки** щелкните список **Поток**.

2. В раскрывающемся списке выберите поток, на который необходимо переключиться.

## <a name="see-also"></a>См. также
- [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)

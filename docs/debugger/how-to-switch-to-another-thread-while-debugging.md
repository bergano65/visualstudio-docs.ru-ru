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
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732445"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Как переключиться на другой поток при отладке в Visual StudioC#(, Visual Basic C++,)
При отладке многопоточного приложения можно использовать любой из нескольких методов для переключения из потока, с которым вы работали, в другой поток.

> [!NOTE]
> Если требуется управлять порядком выполнения потоков, необходимо [заморозить и разморозить потоки](../debugger/get-started-debugging-multithreaded-apps.md).

При проверке потоков в редакторе кода и различных многопоточных окнах отладки, желтая стрелка указывает текущий поток. Зеленая стрелка с фигурным хвостовиком указывает, что нетекущий поток имеет текущий контекст отладчика.

### <a name="to-switch-to-any-thread-that-appears"></a>Переключение на любой появляющийся поток

- В окне "контроль **потоков** или **параллельных вычислений** " дважды щелкните поток.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Переключение на поток в окне исходного кода

- В левом поле щелкните правой кнопкой мыши ![маркер потока](../debugger/media/dbg-thread-marker.png "среадмаркер")значок маркера, выберите пункт **переключиться на**, а затем щелкните имя потока, который необходимо переключить. В контекстном меню отображаются только потоки, работающие с этой конкретной точкой кода.

     Если маркеры потоков не отображаются, щелкните правой кнопкой мыши в окне **потоки** и убедитесь, что выбран параметр **Показывать потоки в источнике** .

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Переключение на поток в панели инструментов "Место отладки"

1. На панели инструментов **место отладки** щелкните список **потоков** .

2. В раскрывающемся списке выберите поток, на который необходимо переключиться.

## <a name="see-also"></a>См. также
- [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)

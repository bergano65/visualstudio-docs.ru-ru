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
ms.openlocfilehash: 163d14de4880ed1c5e2ae6a3170ec5ae1ae47485
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005193"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Как выполнить Переключение на другой поток при отладке в Visual Studio (C#, Visual Basic, C++)
При отладке многопоточных приложений, можно использовать один из нескольких методов для переключения из потока, который вы работали с другому потоку.

> [!NOTE]
> Если вы хотите управлять порядком, в которой выполняются потоки, необходимо [заморозить и Разморозить потоки](../debugger/get-started-debugging-multithreaded-apps.md).

При просмотре потоков в окне редактора кода и различных окон отладки многопоточных желтая стрелка указывает текущий поток. Зеленая стрелка с фигурным концом указывает, что не являющиеся текущими поток имеет контекст текущего отладчика.
  
### <a name="to-switch-to-any-thread-that-appears"></a>Чтобы переключиться на любой поток, который отображается 
  
-   В **потоков** или **контроль параллельных данных** окно, дважды щелкните поток.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Переключение на поток в окне исходного кода  
  
-   В левом поле, щелкните правой кнопкой мыши значок в виде маркера потока ![маркер потока](../debugger/media/dbg-thread-marker.png "ThreadMarker"), пункты **переключиться в режим**, а затем щелкните имя потока, к которому требуется перейти . В контекстном меню отображаются только потоки, работающие с этой конкретной точкой кода.  
  
     Если маркеры потоков не отображается, щелкните правой кнопкой мыши в **потоков** окна и убедитесь, что **Показать потоки в исходном коде** выбран.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Переключение на поток в панели инструментов "Место отладки"  
  
1.  На **место отладки** панели инструментов нажмите кнопку **потоков** списка.  
  
2.  В раскрывающемся списке выберите поток, на который необходимо переключиться.  
  
## <a name="see-also"></a>См. также раздел  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)

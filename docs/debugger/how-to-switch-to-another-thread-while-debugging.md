---
title: Переключение на другой поток при отладке
ms.custom: seodec18
ms.date: 04/27/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45ace6f26f241ecdc39b88060fc4edc6c2e47d91
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057052"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio"></a>Как выполнить Переключение на другой поток при отладке в Visual Studio
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
  
## <a name="see-also"></a>См. также  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)

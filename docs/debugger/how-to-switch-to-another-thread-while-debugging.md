---
title: "Как: переключение на другой поток при отладке | Документы Microsoft"
ms.custom: 
ms.date: 04/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0710bad95484ada62faa042edabf5b76ac459558
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio"></a>Как: переключение на другой поток при отладке в Visual Studio
При отладке многопоточных приложений, можно использовать один из нескольких методов для переключения из потока, который вы работали с на другой поток.

> [!NOTE]
> Если вы хотите управлять порядком, в котором потоки выполняют, необходимо [Замораживание и размораживание потоков](../debugger/get-started-debugging-multithreaded-apps.md).

При рассмотрении потоков в окне редактора кода и различных окон отладки многопоточных желтая стрелка указывает текущий поток. Зеленая стрелка с фигурным концом указывает, что поток не является текущей текущий контекст отладчика.
  
### <a name="to-switch-to-any-thread-that-appears"></a>Чтобы переключиться на любой поток, который отображается 
  
-   В **потоков** или **контроль параллельных данных** окно, дважды щелкните поток.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Переключение на поток в окне исходного кода  
  
-   В поле слева щелкните правой кнопкой мыши значок маркера потока ![маркер потока](../debugger/media/dbg-thread-marker.png "ThreadMarker"), пункты **переключитесь**и щелкните имя потока, к которому требуется перейти . В контекстном меню отображаются только потоки, работающие с этой конкретной точкой кода.  
  
     Если нет маркеры потоков отображается, щелкните правой кнопкой мыши в **потоков** окна и убедитесь, что **Показать потоки в исходном коде** выбран.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Переключение на поток в панели инструментов "Место отладки"  
  
1.  На **место отладки** инструментов, нажмите кнопку **потоков** списка.  
  
2.  В раскрывающемся списке выберите поток, на который необходимо переключиться.  
  
## <a name="see-also"></a>См. также  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)

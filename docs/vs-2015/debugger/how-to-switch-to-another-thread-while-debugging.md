---
title: 'Практическое: переключение на другой поток при отладке | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c682ddff5fd4dc44fe79fa81c1615362f8121e5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568612"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Практическое руководство. Переключение на другой поток при отладке
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: переключиться в другой поток во время отладки](https://docs.microsoft.com/visualstudio/debugger/how-to-switch-to-another-thread-while-debugging).  
  
При отладке многопоточных приложений для переключения контекста с рабочего потока на другой можно использовать один из нескольких способов.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Переключение на любой поток, отображаемый в окне "Потоки"  
  
-   Дважды щелкните поток.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Переключение на поток в окне исходного кода  
  
-   В левом поле, щелкните правой кнопкой мыши индикатор потока, выберите пункт **переключиться в режим**, а затем щелкните имя потока, к которому требуется перейти. В контекстном меню отображаются только потоки, работающие с этой конкретной точкой кода.  
  
     Если индикаторы не отображаются, щелкните правой кнопкой мыши в **потоков** окна и убедитесь, что **Показать потоки в исходном коде** выбран.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Переключение на поток в панели инструментов "Место отладки"  
  
1.  На **место отладки** панели инструментов нажмите кнопку **потоков** поле.  
  
2.  В раскрывающемся списке выберите поток, на который необходимо переключиться.  
  
## <a name="see-also"></a>См. также  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)




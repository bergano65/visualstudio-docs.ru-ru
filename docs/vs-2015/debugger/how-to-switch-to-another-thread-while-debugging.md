---
title: Как переключиться на другой поток во время отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f481a0b1cb2142dc7dbfe11e17ac627753cebf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176510"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Практическое руководство. Переключение на другой поток при отладке
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При отладке многопоточных приложений для переключения контекста с рабочего потока на другой можно использовать один из нескольких способов.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Переключение на любой поток, отображаемый в окне "Потоки"  
  
- Дважды щелкните поток.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Переключение на поток в окне исходного кода  
  
- В левом поле щелкните индикатор потока правой кнопкой мыши, выберите пункт **переключиться на**, а затем щелкните имя потока, в который необходимо переключиться. В контекстном меню отображаются только потоки, работающие с этой конкретной точкой кода.  
  
     Если индикаторы не отображаются, щелкните правой кнопкой мыши в окне **потоки** и убедитесь, что выбран параметр **Показывать потоки в источнике** .  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Переключение на поток в панели инструментов "Место отладки"  
  
1. На панели инструментов **место отладки** щелкните поле **поток** .  
  
2. В раскрывающемся списке выберите поток, на который необходимо переключиться.  
  
## <a name="see-also"></a>См. также:  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)

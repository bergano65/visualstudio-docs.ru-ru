---
title: Отладчику не удается отобразить исходный код или Дизассемблированный код | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2236a585c063194940cf505a0b1d225ae766e2a9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197890"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Отладчику не удается отобразить исходный код или дизассемблированный код
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Текст сообщения об ошибке:  
  
 Отладчику не удается отобразить исходный код или дизассемблированный код для текущего расположения в месте остановки выполнения.  
  
 Это сообщение об ошибке может возникнуть по следующим причинам:  
  
-   Попадание в точку останова в месте, для которого нет исходного кода, при этом язык кода не поддерживает дизассемблированный код. Откройте **точки останова** окна, найдите точку останова и удалите его.  
  
-   При отладке скрипта, возможно, было попадание в точку останова, но в программе в это время не было потоков. Выберите **шаг** или **Продолжить** из **Отладка** для возобновления отладки.  
  
-   Из соображений безопасности отладчик не был допущен к чтению стека, потока, регистра и другой контекстной информации в отлаживаемой программе. Вероятнее всего, это произошло при отладке веб-приложения, и нет корректного разрешения для доступа к виртуальному каталогу. Задайте для безопасности виртуального каталога значение "Анонимный" и повторите попытку.  
  
## <a name="see-also"></a>См. также  
 [Основы отладки](../debugger/debugger-basics.md)   
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)




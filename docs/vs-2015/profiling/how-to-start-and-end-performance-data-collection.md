---
title: Практическое руководство. Начало и окончания сбора данных о производительности | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 15c6d6c904bbab27bac541894ed6cd4f9e1f80f1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60115254"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Практическое руководство. Начало и окончания сбора данных производительности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Прежде чем начать профилирование, необходимо добавить целевой двоичный файл, профилирование которого требуется выполнить в ходе сеанса производительности. Чтобы добавить целевой двоичный файл, щелкните правой кнопкой мыши **Целевые объекты** в **обозревателе производительности**, а затем выберите **Добавить целевой двоичный файл**. В диалоговом окне **Добавление целевого двоичного файла** выберите имя файла и нажмите кнопку **Открыть**. Будет добавлен новый двоичный файл.  
  
### <a name="to-start-profiling"></a>Запуск профилирования  
  
1. Щелкните правой кнопкой мыши имя сеанса производительности в окне **Обозреватель производительности** и выберите один из следующих параметров.  
  
    - **Запустить с профилированием** — запускает приложение и сразу же начинает профилирование.  
  
    - **Запустить с приостановкой профилирования** — запускает приложение, но не начинает профилирование. Чтобы начать профилирование, выберите **Возобновить сбор** в окне **Управление сбором данных**. Дополнительные сведения см. в разделе [Как Приостановка и возобновление сбора данных о производительности](../profiling/how-to-pause-and-resume-performance-data-collection.md).  
  
### <a name="to-end-profiling"></a>Завершение профилирования  
  
- Рекомендуемым методом завершения сеанса профилирования является выход из приложения. Чтобы немедленно остановить профилирование, на панели инструментов **обозревателя производительности** щелкните **Остановить**.  
  
## <a name="see-also"></a>См. также  
 [Управление сбором данных](../profiling/controlling-data-collection.md)   
 [Практическое руководство. Приостановка и возобновление сбора данных о производительности](../profiling/how-to-pause-and-resume-performance-data-collection.md)

---
title: Практическое руководство. Начало и окончания сбора данных о производительности | Документы Майкрософт
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
ms.openlocfilehash: 21697dd4d05b53648a1e77d9b7381973e5583250
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796769"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Практическое руководство. Начало и окончания сбора данных о производительности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Прежде чем начать профилирование, необходимо добавить целевой двоичный файл, профилирование которого требуется выполнить в ходе сеанса производительности. Чтобы добавить целевой двоичный файл, щелкните правой кнопкой мыши **Целевые объекты** в **обозревателе производительности**, а затем выберите **Добавить целевой двоичный файл**. В диалоговом окне **Добавление целевого двоичного файла** выберите имя файла и нажмите кнопку **Открыть**. Будет добавлен новый двоичный файл.  
  
### <a name="to-start-profiling"></a>Запуск профилирования  
  
1.  Щелкните правой кнопкой мыши имя сеанса производительности в окне **Обозреватель производительности** и выберите один из следующих параметров.  
  
    -   **Запустить с профилированием** — запускает приложение и сразу же начинает профилирование.  
  
    -   **Запустить с приостановкой профилирования** — запускает приложение, но не начинает профилирование. Чтобы начать профилирование, выберите **Возобновить сбор** в окне **Управление сбором данных**. Дополнительные сведения см. в статье [How to: Pause and Resume Performance Data Collection](../profiling/how-to-pause-and-resume-performance-data-collection.md) (Практическое руководство. Приостановка и возобновление сбора данных о производительности).  
  
### <a name="to-end-profiling"></a>Завершение профилирования  
  
-   Рекомендуемым методом завершения сеанса профилирования является выход из приложения. Чтобы немедленно остановить профилирование, на панели инструментов **обозревателя производительности** щелкните **Остановить**.  
  
## <a name="see-also"></a>См. также раздел  
 [Управление сбором данных](../profiling/controlling-data-collection.md)   
 [Практическое руководство. Приостановка и возобновление сбора данных о производительности](../profiling/how-to-pause-and-resume-performance-data-collection.md)

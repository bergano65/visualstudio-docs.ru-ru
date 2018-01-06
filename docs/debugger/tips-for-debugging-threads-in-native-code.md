---
title: "Советы по отладке потоков в машинном коде | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fef2f2ab6ad1daf3b24adcda193dce5a3ce3ab17
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Советы по отладке потоков в машинном коде
Ниже приведены некоторые советы по отладке потоков в машинном коде.  
  
-   Можно просмотреть содержимое блока информации потока, введя `@TIB` в **Контрольные значения** окна или **Быстрая проверка** диалоговое окно.  
  
-   Можно просмотреть код последней ошибки текущего потока, введя `@Err` в **Контрольные значения** окна или **Быстрая проверка** диалоговое окно.  
  
-   Для отладки многопоточного приложения можно использовать функции библиотеки времени выполнения C (CRT). Дополнительные сведения см. в разделе [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).  
  
## <a name="see-also"></a>См. также  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)
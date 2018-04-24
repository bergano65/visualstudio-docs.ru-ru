---
title: Советы по отладке потоков в машинном коде | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c98f6bb1a738111d32b26c5b923abe41367e621e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Советы по отладке потоков в машинном коде
Ниже приведены некоторые советы по отладке потоков в машинном коде.  
  
-   Можно просмотреть содержимое блока информации потока, введя `@TIB` в **Контрольные значения** окна или **Быстрая проверка** диалоговое окно.  
  
-   Можно просмотреть код последней ошибки текущего потока, введя `@Err` в **Контрольные значения** окна или **Быстрая проверка** диалоговое окно.  
  
-   Для отладки многопоточного приложения можно использовать функции библиотеки времени выполнения C (CRT). Дополнительные сведения см. в разделе [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).  
  
## <a name="see-also"></a>См. также  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)
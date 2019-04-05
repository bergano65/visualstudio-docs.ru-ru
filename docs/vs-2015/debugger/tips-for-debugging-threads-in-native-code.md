---
title: Советы по отладке потоков в машинном коде | Документация Майкрософт
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
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a0a72f9846add13f2f57581a0b836a9f57f8150
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979279"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Советы по отладке потоков в машинном коде
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ниже приведены некоторые советы по отладке потоков в машинном коде.  
  
-   Можно просмотреть содержимое блока информации потока, введя `@TIB` в окно **Контрольные значения** или диалоговое окно **Быстрая проверка**.  
  
-   Можно просмотреть код последней ошибки текущего потока, введя `@Err` в окно **Контрольные значения** или диалоговое окно **Быстрая проверка**.  
  
-   Для отладки многопоточного приложения можно использовать функции библиотеки времени выполнения C (CRT). Дополнительные сведения см. в разделе [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>См. также  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)

---
title: Советы по отладке потоков в машинном коде | Документация Майкрософт
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 7dde94e28f378f0630a78f32ae5e58533729ce0f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728994"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Советы по отладке потоков в машинном коде
Ниже приведены некоторые советы по отладке потоков в машинном коде.

- Можно просмотреть содержимое блока информации потока, введя `@TIB` в окно **Контрольные значения** или диалоговое окно **Быстрая проверка**.

- Можно просмотреть код последней ошибки текущего потока, введя `@Err` в окно **Контрольные значения** или диалоговое окно **Быстрая проверка**.

- Для отладки многопоточного приложения можно использовать функции библиотеки времени выполнения C (CRT). Дополнительные сведения см. в разделе [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>См. также
- [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)
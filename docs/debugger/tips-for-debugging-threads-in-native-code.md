---
title: Советы по отладке потоков в машинном коде | Документация Майкрософт
description: Список советов по отладке потоков в машинном коде при отладке многопоточных приложений в Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 85bdd804e25dfa91b649e95daacef4bfb322df64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940570"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Советы по отладке потоков в машинном коде
Ниже приведены некоторые советы по отладке потоков в машинном коде.

- Можно просмотреть содержимое блока информации потока, введя `@TIB` в окно **Контрольные значения** или диалоговое окно **Быстрая проверка**.

- Можно просмотреть код последней ошибки текущего потока, введя `@Err` в окно **Контрольные значения** или диалоговое окно **Быстрая проверка**.

- Для отладки многопоточного приложения можно использовать функции библиотеки времени выполнения C (CRT). Дополнительные сведения см. в разделе [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>См. также
- [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)
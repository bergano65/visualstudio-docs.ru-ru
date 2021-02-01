---
title: Нет активности потоков для отображения (представление "Потоки") | Документы Майкрософт
description: Сведения о представлении "Потоки" в ситуациях, когда нет активности для отображения в текущем видимом диапазоне времени.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.nothreadreport
helpviewer_keywords:
- Concurrency Visualizer, No Thread Activity to Show (Threads View)
ms.assetid: aa5ae9d0-561d-4ef8-b36b-258ce553d50a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27298b03a03edf99a12a6d067a22ca8ba17faef0
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722884"
---
# <a name="no-thread-activity-to-show-threads-view"></a>Нет активности потоков для отображения (представление "Потоки")
В этой области отображаются данные о нескрытых потоках в текущем видимом диапазоне времени.

 Если данные не отображаются, проверьте следующие параметры:

- Достаточен ли уровень масштабирования? Попробуйте уменьшить масштаб или прокрутить экран, чтобы отобразить в диапазоне больше потоков.

- Слишком много скрытых потоков? Если это так, то попробуйте отобразить все потоки.

- Если выбран параметр **Только мой код**, можно просматривать данные только для своего кода. Попробуйте снять этот флажок, чтобы узнать, имеется ли активность системных потоков.

- Убедитесь в том, что для снижения шумов выбрано низкое пороговое значение.

## <a name="see-also"></a>См. также
- [Представление потоков](../profiling/threads-view-parallel-performance.md)
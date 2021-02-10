---
title: Остановка внесения изменений в код | Документация Майкрософт
description: Сведения о том, как прекратить применение изменений кода при использовании функции "Изменить и продолжить" во время сеанса отладки Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stop Applying Code Changes command
- code changes, stopping application of
- Edit and Continue, stopping code changes
ms.assetid: 9e72a50c-bb0a-4eaa-9ac1-d00930b68d38
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4aebf3b4a5a7556b2e2a3f6fdff7554539812d8f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896577"
---
# <a name="how-to-stop-code-changes"></a>Практическое руководство. остановку внесения изменений в код
Пока режим "Изменить и продолжить" находится в процессе внесения изменений в код, можно остановить эту операцию.

> [!CAUTION]
> Остановка внесения изменений кода в управляемом коде может привести к непредсказуемым результатам. Внесение изменений в управляемый код – обычно быстрый процесс, поэтому редко есть необходимость его останавливать.

### <a name="to-stop-applying-code-changes"></a>Остановка внесения изменений в код

- Выберите команду **Остановить применение изменений кода** в меню **Отладка**.

  Этот пункт меню становится видимым только в процессе внесения изменений в код.

  При выборе этого параметра никакие изменения в коде не фиксируются.

## <a name="see-also"></a>См. также
- [Изменить и продолжить](../debugger/edit-and-continue.md)
- [Страница "Изменить и продолжить", папка "Отладка", диалоговое окно "Параметры"](./edit-and-continue.md)
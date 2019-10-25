---
title: Диалоговое окно «при попадании в точку останова» | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53b19f4dd0d4b0cb97bb33e4895f36c4dc8f670c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728145"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Диалоговое окно "Попадание в точку останова"
С помощью этого диалогового окна можно произвести настройку действия, выполняемого при достижении точки останова.

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса
 **Печать сообщения** Выводит сообщение с использованием синтаксиса DebuggerDisplay. Дополнительные сведения см. [в разделе Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 Это текстовое поле также поддерживает специальные ключевые слова (например, $ADDRESS), которые можно использовать без дополнительных параметров или заключать в фигурные скобки выражений DebuggerDisplay. Доступные ключевые слова перечислены в диалоговом окне.

 **Продолжить выполнение** Этот элемент управления доступен, только если выбрано **Печать сообщения** . При выборе указанного элемента управления точку останова можно использовать в качестве точки трассировки для отслеживания выполнения программы вместо останова при достижении точки.

## <a name="see-also"></a>См. также
- [Использование точек останова](../debugger/using-breakpoints.md)
- [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
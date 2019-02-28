---
title: Когда точка останова — попаданий диалоговое окно | Документация Майкрософт
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
ms.openlocfilehash: d4cc3c2366ca20328f591b0661e8c2b3e5af1e45
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717706"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Диалоговое окно "Попадание в точку останова"
С помощью этого диалогового окна можно произвести настройку действия, выполняемого при достижении точки останова.

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса
 **Вывод сообщения** печатает сообщение, используя синтаксис DebuggerDisplay. Дополнительные сведения см. в разделе [использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 Это текстовое поле также поддерживает специальные ключевые слова (например, $ADDRESS), которые можно использовать без дополнительных параметров или заключать в фигурные скобки выражений DebuggerDisplay. Доступные ключевые слова перечислены в диалоговом окне.

 **Продолжить выполнение** этот элемент управления включен только тогда, когда **напечатать сообщение** выбран. При выборе указанного элемента управления точку останова можно использовать в качестве точки трассировки для отслеживания выполнения программы вместо останова при достижении точки.

## <a name="see-also"></a>См. также раздел
- [Использование точек останова](../debugger/using-breakpoints.md)
- [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
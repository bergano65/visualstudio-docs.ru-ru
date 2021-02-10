---
title: Диалоговое окно "Попадание в точку останова" | Документация Майкрософт
description: Настройка действия, выполняемого при достижении точки останова, с помощью диалогового окна "При попадании в точку останова". Вы можете задать вывод сообщения с последующим продолжением выполнения.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bfb5099bd0fab17cd983af4e16a435fd192a1668
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883874"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Диалоговое окно "Попадание в точку останова"
С помощью этого диалогового окна можно произвести настройку действия, выполняемого при достижении точки останова.

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса
 **Напечатать сообщение.** Печатает сообщение, используя синтаксис DebuggerDisplay. Дополнительные сведения см. в разделе [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 Это текстовое поле также поддерживает специальные ключевые слова (например, $ADDRESS), которые можно использовать без дополнительных параметров или заключать в фигурные скобки выражений DebuggerDisplay. Доступные ключевые слова перечислены в диалоговом окне.

 **Продолжить выполнение.** Данный элемент управления доступен только в том случае, если выбран параметр **Напечатать сообщение**. При выборе указанного элемента управления точку останова можно использовать в качестве точки трассировки для отслеживания выполнения программы вместо останова при достижении точки.

## <a name="see-also"></a>См. также
- [Использование точек останова](../debugger/using-breakpoints.md)
- [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
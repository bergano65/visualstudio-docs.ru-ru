---
title: Когда точка останова — попаданий диалоговое окно | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 650e390abde6f3ad99e5a0c30591c8d1530df692
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562754"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Диалоговое окно "Попадание в точку останова"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [при точка останова — диалоговое окно попадании](https://docs.microsoft.com/visualstudio/debugger/when-breakpoint-is-hit-dialog-box).  
  
С помощью этого диалогового окна можно произвести настройку действия, выполняемого при достижении точки останова.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Напечатать сообщение**  
 Печатает сообщение, используя синтаксис DebuggerDisplay. Дополнительные сведения см. в разделе [использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Это текстовое поле также поддерживает специальные ключевые слова (например, $ADDRESS), которые можно использовать без дополнительных параметров или заключать в фигурные скобки выражений DebuggerDisplay. Доступные ключевые слова перечислены в диалоговом окне.  
  
 **Продолжить выполнение**  
 Этот элемент управления включен только тогда, когда **напечатать сообщение** выбран. При выборе указанного элемента управления точку останова можно использовать в качестве точки трассировки для отслеживания выполнения программы вместо останова при достижении точки.  
  
## <a name="see-also"></a>См. также  
 [Использование точек останова](../debugger/using-breakpoints.md)   
 [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)




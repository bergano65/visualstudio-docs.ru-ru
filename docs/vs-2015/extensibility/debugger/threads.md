---
title: Потоки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 028ad25495ba01d9763c8bec3bbb9c4480d72ff8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185358"
---
# <a name="threads"></a>Потоки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В плане архитектуры отладчика — это **поток**:  
  
- Является основной единицей вычислений. Поток последовательно выполняет свои инструкции в контексте одного стека вызовов, перемещая из одного контекста кода в следующий.  
  
- Может идентифицировать себя и программу, в которой она выполняется, и может быть именована, приостановлена и возобновлена. Поток также может перечислить связанные с ними фреймы стека, а при некоторых условиях можно переместить в другой кадр стека. При наличии контекста кадра стека поток может вернуть связанный логический поток, если он есть. Поток имеет свойства, такие как число приостановок, которые могут отображаться в окне потоки интегрированной среды разработки.  
  
- Представляется интерфейсом [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , обычно созданным модулем отладки (de) или виртуальной машиной, как следствие выполнения программы.  
  
## <a name="see-also"></a>См. также:  
 [Приложениями](../../extensibility/debugger/programs.md)   
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Модуль отладки](../../extensibility/debugger/debug-engine.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)

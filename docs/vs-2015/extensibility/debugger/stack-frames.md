---
title: Кадры стека | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3050e89db2f5cbb138f3d358b10c7cd936c560e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423391"
---
# <a name="stack-frames"></a>Кадры стека
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В плане архитектуры отладчика **кадр стека**:  
  
- — Это абстракция стека, который предоставляет контекст выполнения потока. Поток всегда выполняется внутри функции. Кадр стека содержит локальные переменные функции и аргументы для нее. Для отладки в Visual Studio язык или окружение, для которых выполняется отладка, должны поддерживать кадры стека.  
  
- Может одновременно идентифицировать и описать себя, а также может возвращать связанный поток. Кадр стека также может возвращать контекст кода, представляющий текущий указатель инструкции, а также связанную документацию и контексты оценки выражений.  
  
- Имеет свойства, описывающие имя, тип и значение локальных переменных и аргументов, которые отображаются в различных окнах отладки интегрированной среды разработки.  
  
- Представляется интерфейсом [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , обычно созданным модулем отладки (de) или виртуальной машиной, как следствие выполнения потока.  
  
## <a name="see-also"></a>См. также:  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Модуль отладки](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)

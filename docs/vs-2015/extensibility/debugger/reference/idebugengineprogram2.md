---
title: IDebugEngineProgram2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c265cbfc89d0b637b1d2f37a3e3b9e948a8dd8f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687789"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс предоставляет поддержку многопоточных отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки реализует этот интерфейс для поддержки одновременная отладка нескольких потоков. Этот интерфейс реализуется на тот же объект, реализующий [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Используйте [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для получения этого интерфейса из `IDebugProgram2` интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugEngineProgram2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Останавливает все потоки, выполняющиеся у этой программы.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Ожидание выполнения (или ожидать выполнения stop) для данного потока.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Разрешает или запрещает вычисления выражения для данного потока, даже если программа остановлена.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio вызывает этот интерфейс в ответ на [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) событий и задание состояний «Контрольные значения для потоков шаг» и «Контрольные значения для выражения вычисления на поток» программы. [Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) вызывается каждый раз, когда нужно остановить программу; этот метод дает программе возможность завершить все потоки.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

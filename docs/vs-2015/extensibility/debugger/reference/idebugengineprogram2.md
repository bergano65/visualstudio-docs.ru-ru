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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687789"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс обеспечивает поддержку многопоточной отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Обработчик отладки реализует этот интерфейс для поддержки одновременной отладки нескольких потоков. Этот интерфейс реализуется на том же объекте, который реализует интерфейс [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Используйте [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для получения этого интерфейса из `IDebugProgram2` интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugEngineProgram2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Останавливает все потоки, выполняющиеся в этой программе.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Отслеживает выполнение (или останавливает наблюдение за выполнением) в заданном потоке.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Разрешает (или запрещает) вычисление выражения в заданном потоке, даже если программа остановлена.|  
  
## <a name="remarks"></a>Remarks  
 Visual Studio вызывает этот интерфейс в ответ на событие [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) и устанавливает состояния программы "отслеживать шаг потока" и "отслеживать оценку выражений в потоке". Метод [остановки](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) вызывается всякий раз, когда программа должна быть остановлена. Этот метод дает программе возможность завершить все потоки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

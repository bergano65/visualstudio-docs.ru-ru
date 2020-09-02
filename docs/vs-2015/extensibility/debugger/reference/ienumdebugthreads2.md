---
title: IEnumDebugThreads2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97bc8383f990f6c0c35a402f2ab36b2595d82a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147683"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфак перечисляет потоки, выполняющиеся в текущем сеансе отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления списка потоков в программе.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) , чтобы получить этот интерфейс, представляющий список всех потоков во всех программах, выполняющихся в процессе. Вызовите [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) , чтобы получить этот интерфейс, представляющий список потоков, выполняющихся в программе.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugThreads2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Извлекает указанное число потоков в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Пропускает указанное число потоков в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Возвращает число потоков в перечислителе.|  
  
## <a name="remarks"></a>Remarks  
 Visual Studio обычно получает этот интерфейс для обновления окна **потоков** , а также для получения первого потока списка для вызова [EXECUTE](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)и [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Первом](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Продолжения](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)

---
title: IEnumDebugThreads2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96a86c322ed2fa1ac750171116a0a11c9b2b4d99
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560706"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IEnumDebugThreads2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugthreads2).  
  
Этого интерфейса перечисляет поток, выполняемый в текущий сеанс отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления списка потоков в программе.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовите [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) для получения этого интерфейса, представляющий список всех потоков во всех программах, выполняющийся в процессе. Вызовите [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) для получения этого интерфейса, представляющий список потоков, выполняющих в программе.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugThreads2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Извлекает указанное число потоков в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Пропускает указанное число потоков в последовательности перечисления.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Получает количество потоков в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio обычно получает этот интерфейс для обновления **потоков** окно также, как получить первый поток списка, чтобы вызвать [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md), и [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)


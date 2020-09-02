---
title: IDebugInterceptExceptionCompleteEvent2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e617e7c19ae126980c0be5473fa279c0f69ff97a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690255"
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс отправляется модулем отладки (DE) в Диспетчер отладки сеансов (SDM) после завершения обработки перехваченного события.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugInterceptExceptionCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Метод DE реализует этот интерфейс для сообщения о том, что обработка перехваченного исключения завершена. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. Модель SDM использует [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для доступа к `IDebugEvent2` интерфейсу.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Параметр DE создает и отправляет этот объект события, чтобы сообщить о завершении перехваченного исключения. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 `IDebugInterceptExceptionCompleteEvent2`Интерфейс реализует следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|Возвращает уникальное значение, связанное с обработанным исключением.|  
  
## <a name="remarks"></a>Remarks  
 Это событие будет отправлено [интерцепткуррентексцептион](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) , когда этот метод успешно завершил обработку перехваченного исключения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)

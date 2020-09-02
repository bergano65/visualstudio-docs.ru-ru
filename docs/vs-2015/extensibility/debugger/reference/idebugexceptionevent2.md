---
title: IDebugExceptionEvent2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f364b6aa622bf9c7481d61e7646e955cebe00933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695399"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Модуль отладки (DE) отправляет этот интерфейс в Диспетчер отладки сеансов (SDM) при возникновении исключения в выполняемой в данный момент программе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Метод DE реализует этот интерфейс для сообщения о том, что в отлаживаемой программе возникло исключение. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. Модель SDM использует [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для доступа к `IDebugEvent2` интерфейсу.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Параметр DE создает и отправляет этот объект события для сообщения об исключении. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugExceptionEvent2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Получает подробные сведения об исключении, которое вызвало это событие.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Возвращает удобное для восприятия описание исключения, которое вызвало это событие.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Определяет, поддерживает ли модуль отладки (DE) возможность передачи этого исключения в отлаживаемую программу при возобновлении выполнения.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Указывает, должно ли исключение передаваться в отлаживаемую программу при возобновлении выполнения или если исключение должно быть отклонено.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Remarks  
 Перед отправкой события метод DE проверяет, было ли событие исключения первым или вторым с помощью предыдущего вызова [сетексцептион](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Если он был определен как первичное исключение, `IDebugExceptionEvent2` событие отправляется в модель SDM. В противном случае параметр DE дает приложению возможность справиться с исключением. Если обработчик исключений не предоставлен, и если исключение было назначено как второе, `IDebugExceptionEvent2` событие отправляется в модель SDM. В противном случае программа отключает выполнение программы, а операционная система или среда выполнения обрабатывает исключение.  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [сетексцептион](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

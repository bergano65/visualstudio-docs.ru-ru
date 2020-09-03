---
title: IEnumDebugFrameInfo2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cc6a0ff332fd6feac72ce4abf38b5319e63c913
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161010"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс перечисляет структуры [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс, чтобы предоставить список структур, описывающих текущий стек вызовов.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Visual Studio вызывает [енумфрамеинфо](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) для получения этого интерфейса всякий раз, когда в отлаживаемой программе происходит точка останова, исключение или остановка.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugFrameInfo2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Извлекает указанное число структур [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Пропускает указанное число структур [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Возвращает число структур [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) в перечислителе.|  
  
## <a name="remarks"></a>Remarks  
 Visual Studio получает этот интерфейс в качестве первого шага для обработки точки останова, исключения или созданной пользователем паузы в отлаживаемой программе. Список структур [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) представляет текущий стек вызовов с текущим вызовом функции в начале списка и самым старым вызовом функции в конце списка. Каждый `FRAMEINFO` представляет кадр стека, контекст, в котором выражения могут оцениваться, и локальные переменные, которые были просмотрены.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [енумфрамеинфо](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)

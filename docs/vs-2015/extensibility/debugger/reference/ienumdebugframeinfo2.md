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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68161010"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс перечисляет [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс, чтобы предоставить список структур, описывающий текущий стек вызовов.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Visual Studio вызывает [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) для получения этого интерфейса, каждый раз, когда точки останова, исключение, или остановка происходит в отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugFrameInfo2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Извлекает указанное число [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структур в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Пропускает заданное число [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структур в последовательности перечисления.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Получает число [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структур в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio получает этот интерфейс в качестве первого шага к обработке точки останова, исключений или пользовательские Пауза вкл отлаживаемой программы. Список [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры представляет текущий стек вызовов, с текущим вызовом функции в начале списка и самая старая функция, вызовите в конце списка. Каждый `FRAMEINFO` представляет кадр стека, контекст, в котором выражения и посмотрели локальных переменных.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)

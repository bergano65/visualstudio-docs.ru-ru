---
title: "IEnumDebugObjects | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c8f62f4a153ac5c5966721578313245fc02f7d04
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс представляет коллекцию объектов, реализующая [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс, чтобы предоставить набора объектов, реализующих [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейса. Обратите внимание, что это не стандартный перечисления COM из-за наличия [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) метод.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс реализует следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Извлекает следующий набор [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекты из перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Пропускает заданное число позиций.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Сбрасывает перечисления в первую запись.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Извлекает копию текущего перечисления.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Возвращает число элементов перечисления.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс позволяет модуля отладки к перечислению набор объектов в массиве.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
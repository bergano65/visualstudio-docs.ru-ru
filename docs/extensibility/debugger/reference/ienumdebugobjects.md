---
title: IEnumDebugObjects | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b76b63aee413b830a468f064647798a13f3d7f99
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895185"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс представляет коллекцию объектов, реализующая [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс для предоставления наборы объектов, реализующих [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейс. Обратите внимание, что это не стандартные перечисление COM из-за наличия [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) метод.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс реализует следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Извлекает следующий набор [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекты из перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Пропускает заданное число позиций.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Сбрасывает перечисление к первой записи.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Извлекает копию текущего перечисления.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Возвращает число элементов перечисления.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс позволяет модуля отладки для перечисления набора объектов в массиве.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
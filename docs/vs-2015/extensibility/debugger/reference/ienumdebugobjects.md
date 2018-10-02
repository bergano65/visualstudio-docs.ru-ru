---
title: IEnumDebugObjects | Документация Майкрософт
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
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3fdb43790d10ffac3fe081369976fe6ee27e0786
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573233"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IEnumDebugObjects](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugobjects).  
  
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
  
|Метод|Описание|  
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


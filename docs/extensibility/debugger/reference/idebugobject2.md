---
title: IDebugObject2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5e60c9e084872b08ec8d38b784b47969af2d52e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс предоставляет дополнительные сведения об объекте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс обеспечивает поддержку для псевдонимов и доступ к информации об объекте.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейса можно получить этот интерфейс, используя [QueryInterface](/cpp/atl/queryinterface). Кроме того [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейс, `IDebugObject2` интерфейс реализует следующие:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Возвращает поля или переменной (если таковые имеются), может выполняться резервное свойство, представленный этим объектом.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Возвращает объект управляемого кода, который представляет значение этого объекта.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Создает уникальный идентификатор для этого объекта или возвращает существующего псевдонима.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Получает псевдоним, связанный с этим объектом, если таковая имеется.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Возвращает тип этого объекта.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Определяет, представляет ли этот объект данных пользователя.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Определяет ли изменить и продолжить состояние больше не является допустимым.<br /><br /> Пользовательских выражений не реализует этот метод (всегда должны возвращать `E_NOTIMPL`).|  
  
## <a name="remarks"></a>Примечания  
 В разделе [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) обсуждение псевдонимы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [Функция GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
---
title: IDebugObject2 | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 4f12376cfeb416b48278f340081fa334a8acdbfc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834712"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс предоставляет дополнительные сведения об объекте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс для предоставления поддержки для псевдонимов и доступ к информации об объекте.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейса можно получить этот интерфейс, используя [QueryInterface](/cpp/atl/queryinterface). Кроме того [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейс, `IDebugObject2` интерфейс реализует следующее:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Получает поле или переменная (если таковые имеются), может резервного свойства, представленного этим объектом.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Получает объект управляемого кода, представляющий значение этого объекта.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Создает уникальный идентификатор для данного объекта или возвращает существующий псевдоним.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Возвращает псевдоним, связанный с данным объектом, если таковые имеются.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Возвращает тип этого объекта.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Определяет, представляет ли этот объект сведений о пользователях.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Определяет ли изменить и продолжить состояние больше не является допустимым.<br /><br /> Вычислитель пользовательское выражение не реализует этот метод (всегда должны возвращать `E_NOTIMPL`).|  
  
## <a name="remarks"></a>Примечания  
 См. в разделе [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) обсуждение псевдонимы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы оценки выражения](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
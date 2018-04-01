---
title: IDebugAlias | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f984f9454aa646663d2888c4241c2ed385188cd7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Представляет числовой псевдоним для переменной. Псевдоним является просто другое имя для переменной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений (Эстония) реализует этот интерфейс для поддержки числовой псевдонимы для переменных.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) создает псевдоним для определенного объекта. Чтобы найти псевдонимы, используйте [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) или [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Следующие методы определяются в `IDebugAlias` интерфейса.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Функция GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Возвращает объект, к которому относится этот псевдоним.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Возвращает имя псевдонима.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Извлекает `ICorDebugValue` интерфейс, обеспечивающий доступ для управляемого кода сведения об этом объекте (только управляемый код).|  
|[Метод Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Помечает данный псевдоним, как больше не используются.|  
  
## <a name="remarks"></a>Примечания  
 Псевдоним — это десятичное число в виде строки, за которым следует символ #, например, 1001#.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
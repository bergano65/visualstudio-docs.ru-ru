---
title: IDebugAlias | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a499cb2d5de9f0507039ec04d31b00d7aaec9ac9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722022"
---
# <a name="idebugalias"></a>IDebugAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Представляет числовые псевдоним для переменной. Псевдоним — это просто другое имя для переменной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений (EE) реализует этот интерфейс для поддержки числовой псевдонимы для переменных.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) создает псевдоним для определенного объекта. Чтобы найти псевдонимы, используйте [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) или [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Следующие методы определяются в `IDebugAlias` интерфейс.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Возвращает объект, к которому относится этот псевдоним.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Возвращает имя псевдонима.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Извлекает `ICorDebugValue` интерфейс, который предоставляет доступ к управляемого кода сведения об этом объекте (только управляемый код).|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Помечает данный псевдоним, как больше не используются.|  
  
## <a name="remarks"></a>Примечания  
 Псевдоним — это десятичное число в виде строки, за которым следует символ #, к примеру, 1001#.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы оценки выражения](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)


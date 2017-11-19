---
title: "IDebugPointerObject | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerObject
helpviewer_keywords: IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df043051ad6c320c14277dc17967365d02cd0197
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс представляет объект указателя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс для представления указателя объект.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейса можно получить этот интерфейс, используя [QueryInterface](/cpp/atl/queryinterface) Если `IDebugObject` представляет указатель.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, наследуемых от [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugPointerObject` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Разыменовать](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Возвращает объект, на который указывает интерфейс.|  
|[Метод GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Возвращает значение, на который указывает интерфейс, как ряд последовательных байтах.|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Задает значение, на который указывает интерфейс из серии последовательных байтов.|  
  
## <a name="remarks"></a>Примечания  
 Вычислитель выражений использует этот интерфейс для представления указателя в дерево синтаксического анализа.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
---
title: IDebugFunctionPosition2 | Документация Майкрософт
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
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 157495b472402d26f67440e2a472723b3fb926ec
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771481"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет позицию по абстрактные функции в исходном документе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления положения функции в исходном документе.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс предоставляется как часть [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union (в частности, [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) структуры), в свою очередь является частью [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Структура, используемая при создании ожидающая точка останова.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugFunctionPosition2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Возвращает имя функции, которая задается по отношению к этой позиции.|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Получает смещение от начала функции.|  
  
## <a name="remarks"></a>Примечания  
 Позиция, представленного этим интерфейсом основана на тексте, в частности, [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) структуры.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)


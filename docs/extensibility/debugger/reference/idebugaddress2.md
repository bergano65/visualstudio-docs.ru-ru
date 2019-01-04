---
title: IDebugAddress2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f8755aae5d349fcb463d7ff2be51ca4015449ac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843980"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Этот интерфейс обеспечивает доступ к Идентификатору процесса, который является владельцем объекта, адрес которого представлен этим интерфейсом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс. Этот интерфейс обеспечивает доступ к Идентификатору процесса, который является владельцем объекта, который связан с этого адреса.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Используйте [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы vtable  
 Помимо методов, наследуемых от [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс, этот интерфейс реализует следующий метод:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Извлекает идентификатор процесса, которому принадлежит объект, представленный этим интерфейсом.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
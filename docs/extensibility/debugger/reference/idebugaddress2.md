---
title: IDebugAddress2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 43c112da892fadf95eb5a27880d82ec9d29419c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugaddress2"></a>IDebugAddress2
Этот интерфейс обеспечивает доступ к идентификатор процесса, который является владельцем объекта, адрес которого представлен этот интерфейс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейса. Этот интерфейс предоставляет доступ к идентификатор процесса, который является владельцем объекта, связанного с этим адресом.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Используйте [QueryInterface](/cpp/atl/queryinterface) получить этот интерфейс из [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы vtable  
 Помимо методов, наследуемых от [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс, этот интерфейс реализует следующий метод:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Извлекает идентификатор процесса, который является владельцем объекта, представленного этим интерфейсом.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
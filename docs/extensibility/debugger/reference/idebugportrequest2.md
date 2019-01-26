---
title: IDebugPortRequest2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 218aef6d65578d67fdc14f61aa090c81476c25af
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975748"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Этот интерфейс описывает порт. Это описание используется, чтобы добавить порт поставщика порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio обычно реализует этот интерфейс находится в процессе получения из поставщика порта отладки.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс, передается в [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) создать порт отладки. Вызов [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) возвращает этот интерфейс, представляющий запрос, используемый для создания порта в первую очередь.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugPortRequest2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Получает имя порта для создания.|  
  
## <a name="remarks"></a>Примечания  
 Модуль отладки обычно не взаимодействует с поставщика порта и не понадобится для данного интерфейса.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
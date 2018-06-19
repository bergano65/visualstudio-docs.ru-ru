---
title: IDebugPortNotify2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1874b46e702af49bf8f0a738b9e764f2fa11014
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115181"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Этот интерфейс регистрирует или отменяет регистрацию программы, можно отлаживать с порт, к которому он выполняется.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Поставщик пользовательский порт реализует этот интерфейс для поддержки добавления и удаления программ из порта. Обычно реализуется на тот же объект, реализующий [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов [QueryInterface](/cpp/atl/queryinterface) на `IDebugPort2` интерфейс возвращает этот интерфейс. Кроме того, вызов [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) возвращает этот интерфейс. Модуль отладки можно увидеть этот интерфейс как параметр [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugPortNotify2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Регистрирует программу, которая может отлаживаться порт, к которому он выполняется.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Отменяет регистрацию программы, можно отлаживать из порта, запущенного на.|  
  
## <a name="remarks"></a>Примечания  
 Если порт отладки нет способа узнать, при загрузке или выгрузке программы, поставщик другой номер порта должен реализовывать этот интерфейс. Все программы, которые загружаются при отладке через определенный порт, отслеживаются с помощью этого интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
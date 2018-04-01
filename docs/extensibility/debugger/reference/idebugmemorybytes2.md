---
title: IDebugMemoryBytes2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9a6377ff5ba61427269df683b34a20292c441632
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Этот интерфейс представляет байт памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления байтов в памяти.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) возвращает этот интерфейс для предоставления доступа к системной памяти. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) и [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) возвращают этот интерфейс для предоставления доступа к объекта байтов.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugMemoryBytes2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Считывает последовательность байтов, начиная с заданной позиции.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Записывает `dwCount` байт, начиная с `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Возвращает размер памяти в байтах, представляемые данным интерфейсом.|  
  
## <a name="remarks"></a>Примечания  
 Для свойств [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) предоставляет интерфейс, представляющий массив `IDebugMemoryBytes2` интерфейс для доступа к значениям в этом массиве.  
  
 Visual Studio **памяти представление** вызовы [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) для получения `IDebugMemoryBytes2` интерфейс для доступа к системной памяти. Получение адреса должен быть предоставлен доступ, синтаксический анализ выражения, введенные как адрес в памяти представление и затем оценивая проанализированное выражение с помощью [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для получения `IDebugProperty2` интерфейса. Вызов [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) возвращает [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , описывающий адрес памяти. Этот контекст памяти затем передается [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) и [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
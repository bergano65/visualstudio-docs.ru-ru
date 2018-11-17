---
title: IDebugMemoryBytes2 | Документация Майкрософт
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
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddbe101efe069787bbbb2ad6462c87bc1151c0cd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751957"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет байт памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления байтов в памяти.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) возвращает этот интерфейс для предоставления доступа к системной памяти. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) и [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) возвращают этот интерфейс для предоставления доступа к объекта байтов.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugMemoryBytes2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Считывает последовательность байтов, начиная с заданного расположения.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Записывает `dwCount` байт, начиная с `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Возвращает размер в байтах, памяти, представленного этим интерфейсом.|  
  
## <a name="remarks"></a>Примечания  
 Для свойств [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) предоставляет интерфейс, представляющий массив `IDebugMemoryBytes2` интерфейс для доступа к значениям в этом массиве.  
  
 Visual Studio **представление памяти** вызовы [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) извлекаемого `IDebugMemoryBytes2` интерфейс для доступа к системной памяти. Получение адреса для доступа, синтаксический анализ выражения, введенные в виде адреса в памяти представление и затем оценивая проанализированное выражение, использующее [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для получения `IDebugProperty2` интерфейс. Вызов [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) возвращает [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , описывающий адрес памяти. Затем передается этот контекст памяти [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) и [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
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


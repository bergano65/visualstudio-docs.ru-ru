---
title: Интерфейс IJsDebugDataTarget | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e14046443ca0560deacb6ddb6e39b1fc25d18fea
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097426"
---
# <a name="ijsdebugdatatarget-interface"></a>Интерфейс IJsDebugDataTarget
Реализуется отладчиком для предоставления функциональности для получения и изменения состояния целевого процесса отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[Метод IJsDebugDataTarget::AllocateVirtualMemory](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Резервирует и(или) фиксирует область памяти в пространстве виртуальных адресов целевого процесса.|  
|[Метод IJsDebugDataTarget::CreateStackFrameEnumerator](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Создает перечислитель для кадров стека.|  
|[Метод IJsDebugDataTarget::FreeVirtualMemory](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Выпускает и(или) отменяет фиксацию области памяти в пространстве виртуальных адресов целевого процесса.|  
|[Метод IJsDebugDataTarget::GetThreadContext](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Возвращает контекст для данного потока.|  
|[Метод IJsDebugDataTarget::GetTlsValue](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Для отлаживаемого потока извлекает значение в области потока локальное хранилище (TLS) для указанного индекса TLS.|  
|[Метод IJsDebugDataTarget::ReadBSTR](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Читает BSTR из целевого объекта отладки.|  
|[Метод IJsDebugDataTarget::ReadMemory](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Читает содержимое памяти целевого процесса.|  
|[Метод IJsDebugDataTarget::ReadNullTerminatedString](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Считывает указанное количество символов из целевого объекта.|  
|[Метод IJsDebugDataTarget::WriteMemory](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Читает содержимое памяти целевого процесса.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)
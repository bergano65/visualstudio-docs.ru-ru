---
title: Интерфейс метод ijsdebugdatatarget | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c77209230abfe261c9ec0b884ad0a677cfbf07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572452"
---
# <a name="ijsdebugdatatarget-interface"></a>Интерфейс IJsDebugDataTarget
Реализуется отладчиком для предоставления функциональных возможностей доступа и изменения состояния целевого процесса отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="public-methods"></a>Открытые методы  
  
|Название|Описание|  
|----------|-----------------|  
|[Метод IJsDebugDataTarget::AllocateVirtualMemory](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Резервирует или фиксирует область памяти в виртуальном адресном пространстве целевого процесса.|  
|[Метод IJsDebugDataTarget::CreateStackFrameEnumerator](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Создает перечислитель для кадров стека.|  
|[Метод IJsDebugDataTarget::FreeVirtualMemory](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Выпуски или отменяют выделение области памяти в виртуальном адресном пространстве целевого процесса.|  
|[Метод IJsDebugDataTarget::GetThreadContext](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Извлекает контекст для данного потока.|  
|[Метод IJsDebugDataTarget::GetTlsValue](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Для отлаживаемого потока получает значение в слоте локального хранилища потока (TLS) для указанного индекса TLS.|  
|[Метод IJsDebugDataTarget::ReadBSTR](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Считывает строку BSTR из целевого объекта отладки.|  
|[Метод IJsDebugDataTarget::ReadMemory](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Считывает память целевого процесса.|  
|[Метод IJsDebugDataTarget::ReadNullTerminatedString](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Считывает указанное количество символов из целевого объекта.|  
|[Метод IJsDebugDataTarget::WriteMemory](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Считывает память целевого процесса.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)
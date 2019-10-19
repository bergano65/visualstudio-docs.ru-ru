---
title: 'Метод метод ijsdebugdatatarget:: WriteMemory | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cd23ad784e222f770dfd5c0e7c2d775aa55e42
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572416"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>Метод IJsDebugDataTarget::WriteMemory
Считывает память целевого процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `address`  
 окне Базовый адрес, из которого записывается память целевого процесса.  
  
 `pMemory`  
 окне Данные, записываемые в адресное пространство указанного процесса.  
  
 `size`  
 окне Число байтов, записываемых в процесс.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Заметки  
 Перед передачей данных система проверяет, чтобы все данные в базовом адресе и памяти указанного размера были доступны для доступа на запись, и если она недоступна, функция вызывает ошибку E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)
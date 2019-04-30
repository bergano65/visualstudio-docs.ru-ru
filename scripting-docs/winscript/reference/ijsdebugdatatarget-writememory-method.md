---
title: Метод IJsDebugDataTarget::WriteMemory | Документация Майкрософт
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
ms.openlocfilehash: 622de16cc5f755c5d69059a0e0f28d881121861c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558181"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>Метод IJsDebugDataTarget::WriteMemory
Читает содержимое памяти целевого процесса.  
  
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
 [in] Базовый адрес, по которым следует записывать память целевого процесса.  
  
 `pMemory`  
 [in] Данные для записи в адресном пространстве указанного процесса.  
  
 `size`  
 [in] Число байтов для записи в текущий процесс.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Прежде чем происходит передача данных, система проверяет, что все данные в базовый адрес и память указанного размера доступны для записи, и если он недоступен, функция вызывает ошибку E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)
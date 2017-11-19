---
title: "Метод IJsDebugDataTarget::WriteMemory | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed562c1cbdd645da6cca87e45f272c25f8bc0d4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetwritememory-method"></a>Метод IJsDebugDataTarget::WriteMemory
Считывает память целевого процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `address`  
 [in] Базовый адрес для записи в память целевого процесса.  
  
 `pMemory`  
 [in] Данные будут записываться в адресное пространство указанного процесса.  
  
 `size`  
 [in] Число байтов для записи в процессе.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Прежде чем произойдет передача данных, система проверяет, что все данные в базовый адрес и памяти указанного размера будут доступны для записи, и если он недоступен, функция вызывает ошибку E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)
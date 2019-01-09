---
title: Метод IJsDebugDataTarget::WriteMemory | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a2dfc8db8d79dbca388b1792a58169b7dbe17151
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089288"
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
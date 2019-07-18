---
title: Метод IJsDebug::OpenVirtualProcess | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97a055bf1550d74dc6b86d93ffdb9ca406afb43d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583598"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>Метод IJsDebug::OpenVirtualProcess
Фабричный метод, используемый для создания нового объекта виртуального процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `processId`  
 [in] Идентификатор процесса, чтобы присоединить отладчик.  
  
 `runtimeJsBaseAddress`  
 [in] Базовый адрес, по которому среда выполнения JavaScript загружена в целевом процессе.  
  
 `pDataTarget`  
 [in] Предоставленный интерфейс для запроса состояния процесса отладчика.  
  
 `ppProcess`  
 [out] Новый объект процесса отладки  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Возвращает E_JsDEBUG_MISMATCHED_RUNTIME при Jscript9diag и Jscript9 не совпадают.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebug](../../winscript/reference/ijsdebug-interface.md)
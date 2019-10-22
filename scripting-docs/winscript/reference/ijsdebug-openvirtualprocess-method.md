---
title: 'Метод Ижсдебуг:: OpenVirtualProcess | Документация Майкрософт'
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
ms.openlocfilehash: 3de39beb28a68ec3b8e0d76b17a7e914a464ecfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577748"
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
 окне Идентификатор процесса, к которому следует присоединить отладчик.  
  
 `runtimeJsBaseAddress`  
 окне Базовый адрес, по которому среда выполнения JavaScript загружена в целевой процесс.  
  
 `pDataTarget`  
 окне Предоставляемый отладчиком интерфейс для запроса состояния процесса.  
  
 `ppProcess`  
 заполняет Новый объект процесса отладки  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Заметки  
 Возвращает E_JsDEBUG_MISMATCHED_RUNTIME, если Jscript9diag и JScript9 не совпадают.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebug](../../winscript/reference/ijsdebug-interface.md)
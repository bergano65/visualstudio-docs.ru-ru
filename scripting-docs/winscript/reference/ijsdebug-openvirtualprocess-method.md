---
title: Метод IJsDebug::OpenVirtualProcess | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f5acb137337e46a6e84f7d68c9330a3ca847f2e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727364"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>Метод IJsDebug::OpenVirtualProcess
Фабричный метод, используемый для создания нового объекта виртуального процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `processId`  
 [in] Идентификатор процесса для присоединения отладчика.  
  
 `runtimeJsBaseAddress`  
 [in] Базовый адрес, по которому загрузки среды выполнения JavaScript в целевом процессе.  
  
 `pDataTarget`  
 [in] Предоставленный интерфейс для запроса состояния процесса отладчика.  
  
 `ppProcess`  
 [out] Новый объект процесса отладки  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Возвращает E_JsDEBUG_MISMATCHED_RUNTIME, если Jscript9diag и Jscript9 не совпадают.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebug](../../winscript/reference/ijsdebug-interface.md)
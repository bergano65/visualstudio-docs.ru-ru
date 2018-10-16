---
title: IDebugModOpt::GetModOpts | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4be7cf2239b77314646df8285d1a89953f9401fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112386"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Получает список необязательных модификаторов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetModOpts(  
   ULONG  celt,  
   BSTR*  rgelt,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetModOpts(  
   uint         celt,  
   out string[] rgelt,  
   ref uint     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Число элементов, которые должны быть возвращены.  
  
 `rgelt`  
 [out] Возвращает массив, содержащий параметры.  
  
 `pceltFetched`  
 [in, out] Число элементов, возвращаемых в `rgelt` массива.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
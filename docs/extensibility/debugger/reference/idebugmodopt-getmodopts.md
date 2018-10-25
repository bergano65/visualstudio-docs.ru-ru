---
title: IDebugModOpt::GetModOpts | Документация Майкрософт
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
ms.openlocfilehash: db00126b72399610e0e270c1cd0f736171f52fce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903508"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Возвращает список необязательных модификаторов.  
  
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
 [in, out] Количество элементов, возвращаемых в `rgelt` массива.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
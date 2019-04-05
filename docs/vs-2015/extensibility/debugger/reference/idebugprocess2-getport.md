---
title: IDebugProcess2::GetPort | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetPort
helpviewer_keywords:
- IDebugProcess2::GetPort
ms.assetid: e39b6e5a-64eb-48cf-a53d-da4fdb968e2d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d77310abb6643ef6e9c17c21b5199d5889b1492
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990280"
---
# <a name="idebugprocess2getport"></a>IDebugProcess2::GetPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает порт, на которой выполняется процесс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetPort(   
   IDebugPort2** ppPort  
);  
```  
  
```csharp  
int GetPort(   
   out IDebugPort2 ppPort  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppPort`  
 [out] Возвращает [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) объект, который представляет порт, на котором был запущен процесс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

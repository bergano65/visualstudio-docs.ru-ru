---
title: IDebugProgram2::GetENCUpdate | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 83b4a22d8cfb1d8ab89adb5946305ea50425fa35
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114801"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Этот метод возвращает изменить и продолжить (ENC) обновления для этой программы. Всегда возвращает модулем отладки `E_NOTIMPL`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetENCUpdate(   
   IUnknown** ppUpdate  
);  
```  
  
```csharp  
int GetENCUpdate(  
   out object ppUpdate  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppUpdate`  
 [out] Возвращает внутренний интерфейс, который может использоваться для обновления этой программы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
> [!NOTE]
>  Всегда должны возвращать модулем отладки `E_NOTIMPL`.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
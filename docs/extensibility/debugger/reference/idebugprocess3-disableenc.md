---
title: IDebugProcess3::DisableENC | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c8d440783dbd6112e6f9918cd22388b4b8efbff0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921195"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Этот метод явно отключает Изменить и продолжить об этом процессе (и все программы, он содержит). Поставщик пользовательский порт, всегда должны возвращать `E_NOTIMPL`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```csharp  
   EncUnavailableReason reason  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `reason`  
 [in] Значение из [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
> [!NOTE]
>  Поставщик пользовательский порт, всегда должны возвращать `E_NOTIMPL`.  
  
## <a name="remarks"></a>Примечания  
 Один раз изменить и продолжить отключен для процесса, его можно снова включить только путем перезапуска процесса.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
---
title: "IDebugProcess3::DisableENC | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::DisableENC
helpviewer_keywords: IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fba3718052b708b5c5d88306c022ed9c397a99cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Этот метод явно отключает Изменить и продолжить по этому процессу (и все программы содержит). Всегда должны возвращать поставщика пользовательских порта `E_NOTIMPL`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
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
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
> [!NOTE]
>  Всегда должны возвращать поставщика пользовательских порта `E_NOTIMPL`.  
  
## <a name="remarks"></a>Примечания  
 Один раз изменить и продолжить отключена для процесса, его можно снова включить только путем перезапуска процесса.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
---
title: IDebugProcess3::D Исаблинк | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0db9eb44b8074a5c5e3b35a5a5dadcf04f37fb2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842745"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод явно отключает функцию "изменить и продолжить" для этого процесса (и всех содержащихся в нем программ). Пользовательский поставщик порта всегда должен возвращать значение `E_NOTIMPL` .  
  
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
 окне Значение из перечисления [енкунаваилаблереасон](../../../extensibility/debugger/reference/encunavailablereason.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.  
  
> [!NOTE]
> Пользовательский поставщик порта всегда должен возвращать значение `E_NOTIMPL` .  
  
## <a name="remarks"></a>Remarks  
 Если для процесса отключена возможность "изменить и продолжить", ее можно включить заново, только перезапустив процесс.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)

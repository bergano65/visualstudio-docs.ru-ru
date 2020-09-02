---
title: 'IDebugPendingBreakpoint2:: Сетпасскаунт | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42a4c4b008b34a66a408cbb9a5615ae3fbbf8407
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188604"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает или изменяет число проходов, связанных с ожидающей точкой останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bpPassCount`  
 окне Структура [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) , содержащая число проходов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает значение `E_BP_DELETED` , если точка останова была удалена.  
  
## <a name="remarks"></a>Remarks  
 Все счетчики пройденных, которые ранее были связаны с ожидающей точкой останова, теряются. Все точки останова, привязанные к этой ожидающей точке останова, вызываются для установки их счетчика проходов в `bpPassCount` параметре.  
  
## <a name="see-also"></a>См. также:  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)

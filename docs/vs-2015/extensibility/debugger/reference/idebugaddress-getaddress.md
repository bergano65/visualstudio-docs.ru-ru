---
title: 'Идебугаддресс:: @ Address | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4d3263ca020f491e0c1cf20ee49792cacfbc362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186687"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает структуру, описывающую объект и его расположение в области или контейнере.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pAddress`  
 [вход, выход] Структура [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) , которая заполняется этим методом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Структура [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) передается в этот метод, который затем заполняет его соответствующими данными. Способ интерпретации этой информации зависит от типа возвращаемой информации и самого обработчика символов. Дополнительные сведения см. в разделе [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .  
  
## <a name="see-also"></a>См. также:  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)

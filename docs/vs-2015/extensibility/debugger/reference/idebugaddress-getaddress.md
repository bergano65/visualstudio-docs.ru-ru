---
title: IDebugAddress::GetAddress | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddb3b6e3d8055dd9a5b6304cf57a355986706b0d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186768"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает структуру, описывающий объект и его расположение в пределах ее области или контейнера.  
  
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
 [in, out] Объект [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структуру, которая заполняется с помощью данного метода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структуры передается этому методу, который затем заполняет его с помощью соответствующую информацию. Способ интерпретации этой информации зависит от типа возвращаемых сведений и сам обработчик символов. См. в разделе [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) для получения дополнительных сведений.  
  
## <a name="see-also"></a>См. также  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)


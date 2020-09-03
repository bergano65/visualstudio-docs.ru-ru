---
title: 'Идебугфиелд:: GetTypeInfo | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4229bef0460c7475cda3f81d06b6b24e38ed759
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148901"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод получает независимые от типа сведения о символе или типе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```csharp  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pTypeInfo`  
 заполняет Возвращает сведения о типе в указанной структуре [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Независимые от типа сведения включают, например, AppDomain, модуль и класс, содержащий символ.  
  
## <a name="see-also"></a>См. также:  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)

---
title: 'IDebugProperty2:: IsReference | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73f6bb556c3f18c8327985ac7c46b77a3a6d2c01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193482"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает ссылку на значение свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetReference(  
   IDebugReference2** ppReference  
);  
```  
  
```csharp  
int GetReference(  
   out IDebugReference2 ppReference  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppRererence`  
 заполняет Возвращает объект [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , представляющий ссылку на значение свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки, обычно `E_NOTIMPL` или `E_GETREFERENCE_NO_REFERENCE` .  
  
## <a name="see-also"></a>См. также:  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

---
title: 'Идебугженерикфиелдинстанце:: Типеаргументкаунт | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 80c2aea4130fe7de0208d4c40b0f01afed06eecf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180848"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает число аргументов параметра типа для данного экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT TypeArgumentCount(  
   ULONG32* pcArgs  
);  
```  
  
```csharp  
int TypeArgumentCount(  
   ref uint pcArgs  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcArgs`  
 [вход, выход] Число аргументов параметра типа для данного экземпляра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Например, если List \<int> , этот метод возвращает значение 1, а если List \<int,float2> возвращает значение 2. Этот метод возвращает 0, если отсутствуют аргументы типа.  
  
## <a name="see-also"></a>См. также:  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)

---
title: IDebugGenericParamField::GetIndex | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugGenericParamField::GetIndex
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 859764a8673c953e3a2dffa06219349e8f76db6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggenericparamfieldgetindex"></a>IDebugGenericParamField::GetIndex
Возвращает индекс этого универсального параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetIndex(  
   DWORD* pIndex  
);  
```  
  
```csharp  
int GetIndex(  
   out uint pIndex  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pIndex`  
 [out] Значение этого универсального параметра индекса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Например для Dictionary(K,V), K имеет индекс 0, V имеет индекс 1.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CDebugGenericParamFieldType** объекта, который предоставляет [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) интерфейса.  
  
```cpp  
HRESULT CDebugGenericParamFieldType::GetIndex(DWORD* pIndex)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetIndex );  
  
    IfFalseGo(pIndex, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pIndex = m_index;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetIndex, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
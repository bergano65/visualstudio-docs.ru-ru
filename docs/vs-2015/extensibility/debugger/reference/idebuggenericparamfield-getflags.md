---
title: 'Флаги Идебугженерикпарамфиелд:: "|" Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetFlags
- IDebugGenericParamField::GetFlags
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1fb4ecc3f09e4ffa8a8811867c9957ac685c76ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180710"
---
# <a name="idebuggenericparamfieldgetflags"></a>IDebugGenericParamField::GetFlags
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает флаги для этого универсального параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetFlags(  
   DWORD* pdwFlags  
);  
```  
  
```csharp  
int GetFlags(  
   ref uint pdwFlags  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwFlags`  
 заполняет Возвращает флаги для этого универсального параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Эти флаги содержат сведения о различных специальных ограничениях.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для объекта **кдебугженерикпарамфиелдтипе** , предоставляющего интерфейс [идебугженерикпарамфиелд](../../../extensibility/debugger/reference/idebuggenericparamfield.md) .  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );  
  
    IfFalseGo( pdwFlags, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pdwFlags = m_dwFlags;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)

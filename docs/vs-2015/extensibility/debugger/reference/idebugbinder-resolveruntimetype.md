---
title: 'Идебугбиндер:: Ресолверунтиметипе | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 69b1418c76e01b87bcd6d992a82ce58287e79ceb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192293"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод определяет тип времени выполнения объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```csharp  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pObject`  
 окне [Идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , который необходимо разрешить.  
  
 `ppResolved`  
 заполняет Возвращает тип объекта в виде [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Тип времени выполнения объекта не всегда известен во время компиляции. Например, с помощью полиморфизма аргумент может быть передан в функцию в качестве базового класса, например класса Button. Фактический аргумент может быть производным классом, например классом переключателя.  
  
## <a name="see-also"></a>См. также:  
 [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md)   
 [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

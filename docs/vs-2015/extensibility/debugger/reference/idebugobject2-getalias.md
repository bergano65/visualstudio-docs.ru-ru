---
title: IDebugObject2::/Alias | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b05d416da41265f6727df843b1b686fcfe5107f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194613"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает псевдоним, связанный с этим объектом, если он есть.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppAlias`  
 заполняет Возвращает объект [идебугалиас](../../../extensibility/debugger/reference/idebugalias.md) , представляющий псевдоним для данного объекта. в противном случае возвращает значение null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Псевдоним для объекта создается с помощью вызова метода [креатеалиас](../../../extensibility/debugger/reference/idebugobject2-createalias.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

---
title: 'IDebugBinder3:: Финдалиас | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47aaaec73d2c364e974b7430335404bf8caf406c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68142958"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод находит псевдоним по заданному имени. При этом будут искаться все псевдонимы в программе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcstrName`  
 окне Имя искомого псевдонима.  
  
 `ppAlias`  
 заполняет Найден псевдоним (если имеется), представленный интерфейсом [идебугалиас](../../../extensibility/debugger/reference/idebugalias.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает значение `S_FALSE` (если псевдоним не найден) или код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод инициализирует целевой объект до значения null перед вызовом метода; После этого проверяется наличие значения NULL, чтобы определить, был ли найден псевдоним.  
  
## <a name="see-also"></a>См. также:  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

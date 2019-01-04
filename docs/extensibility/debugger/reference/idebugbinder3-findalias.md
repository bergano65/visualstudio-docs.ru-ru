---
title: IDebugBinder3::FindAlias | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 361e23ebe7f9311139a96a1188e3e13474c93f19
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838691"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Этот метод осуществляет поиск псевдоним, заданному имени. Таким образом, найти все псевдонимы в программе.  
  
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
 [in] Имя псевдонима для поиска.  
  
 `ppAlias`  
 [out] Представленный псевдоним, найденный (если таковые имеются) [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) интерфейс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` (Если псевдоним не найден) или код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод инициализирует в целевой объект, значение null перед вызовом метода; Затем проверяется значение null, впоследствии определить, был ли найден псевдоним.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
---
title: IDebugBinder3::FindAlias | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: e68038f6e00c2a04f4c96f5f9d93fc4919d2fd09
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102126"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Этот метод осуществляет поиск псевдоним, заданному имени. Выполняется поиск всех псевдонимов в программе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcstrName`  
 [in] Имя псевдонима для поиска.  
  
 `ppAlias`  
 [out] Представленный псевдоним обнаружен (если таковые имеются) [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) интерфейса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` (Если псевдоним не найден) или код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод инициализирует целевой объект значение null перед вызовом метода; Затем выполняется проверка значения null впоследствии определить, был ли найден псевдоним.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
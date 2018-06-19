---
title: IDebugAlias::GetICorDebugValue | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bfe0d8e4734c0d836b2dc6009fdedfa264720778
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099055"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Извлекает интерфейс управляемого кода, который представляет значение, связанное с данным псевдонимом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppUnk`  
 [out] `IUnknown` интерфейс, который представляет значение, связанное с данным псевдонимом. Этот интерфейс можно запрашивать `ICorDebugValue` интерфейса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод применим только в управляемых значения ( `ICorDebugValue` доступен интерфейс в [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] и определяется в [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK в файле CorDebug.IDL).  
  
## <a name="see-also"></a>См. также  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
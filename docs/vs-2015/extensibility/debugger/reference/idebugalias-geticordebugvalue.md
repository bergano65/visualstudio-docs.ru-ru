---
title: 'Идебугалиас:: Жетикордебугвалуе | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67ab8a7343cd320470515b757dfca905a0a4690e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156278"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает интерфейс управляемого кода, представляющий значение, связанное с этим псевдонимом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppUnk`  
 [out] `IUnknown` интерфейс, представляющий значение, связанное с этим псевдонимом. Этот интерфейс можно запрашивать для `ICorDebugValue` интерфейса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод применяется только к управляемым значениям ( `ICorDebugValue` интерфейс доступен в и определяется [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] в [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] пакете SDK в файле CorDebug. IDL).  
  
## <a name="see-also"></a>См. также:  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

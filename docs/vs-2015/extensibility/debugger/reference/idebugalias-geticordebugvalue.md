---
title: IDebugAlias::GetICorDebugValue | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81b9f024b8b8e66185d2d8852e7e530958061b74
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568938"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugAlias::GetICorDebugValue](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugalias-geticordebugvalue).  
  
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
 [out] `IUnknown` интерфейс, который представляет значение, связанное с данным псевдонимом. Этот интерфейс может запрашиваться для `ICorDebugValue` интерфейс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод применим только к значениям управляемых ( `ICorDebugValue` доступен интерфейс в [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] и определен в [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] пакета SDK в файле CorDebug.IDL).  
  
## <a name="see-also"></a>См. также  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)


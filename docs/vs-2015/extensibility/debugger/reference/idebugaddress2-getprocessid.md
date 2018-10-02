---
title: IDebugAddress2::GetProcessID | Документация Майкрософт
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
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31c935db12a3cbac5bf4e85800e826e1972be4f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563923"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugAddress2::GetProcessID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugaddress2-getprocessid).  
  
Извлекает идентификатор процесса, которому принадлежит объект, представленный этим [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) интерфейс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```csharp  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pProcID`  
 [out] Идентификатор процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)


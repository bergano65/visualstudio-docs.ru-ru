---
title: IDebugAddress2::GetProcessID | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 96f6eb7ff4241def9b612a46ecc735eb90e2e9e8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276592"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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


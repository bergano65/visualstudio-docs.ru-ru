---
title: IDebugDefaultPort2::QueryIsLocal | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cec66860bb75cb62e71e2924ed728e1bd86ad59f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Этот метод определяет, является ли этот порт на локальном компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```csharp  
int QueryIsLocal();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` локального (на том же компьютере, что и вызывающий объект) Если этот порт или `S_FALSE` Если порт находится на другом компьютере.  
  
## <a name="see-also"></a>См. также  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
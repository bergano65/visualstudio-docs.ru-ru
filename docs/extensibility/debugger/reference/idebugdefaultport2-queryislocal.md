---
title: IDebugDefaultPort2::QueryIsLocal | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d52ee13002cc53084bc4f81b8cb65d489f3932d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
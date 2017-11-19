---
title: "IDebugProcessSecurity::QueryCanSafelyAttach | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ad6b7ffde868bf6b9dc4f9ef3bab9d9094ab765
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Этот метод позволяет поставщика порта, чтобы отображалось предупреждение, прежде чем пользователь присоединяет к процессу unsafe.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Существуют следующие возвращаемые значения.  
  
-   `S_OK`: Присоединение к процессу можно безопасно и диалоговое окно предупреждение не отображается.  
  
-   `S_FALSE`: Присоединение возможно, проблемы безопасности и отображается диалоговое окно с предупреждением.  
  
-   `FAILURE`: Происходит сбой присоединение к процессу.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
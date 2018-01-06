---
title: "IDebugModule3::SetJustMyCodeState | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3::SetJustMyCodeState
helpviewer_keywords: IDebugModule3::SetJustMyCodeState
ms.assetid: 68f8166d-ef64-49ae-ad5e-79604f43bbd4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 48ffa09b66ee789526a2c6b99c57bf9d500f2c61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule3setjustmycodestate"></a>IDebugModule3::SetJustMyCodeState
Помечает модуль как пользовательский код или нет.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL fIsUserCode  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int fIsUserCode  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fIsUserCode`  
 [in] Ненулевое значение (`TRUE`), если модуль следует рассматривать как код пользователя, ноль (`FALSE`) Если не следует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
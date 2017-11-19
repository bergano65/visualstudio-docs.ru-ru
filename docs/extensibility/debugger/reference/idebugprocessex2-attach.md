---
title: "IDebugProcessEx2::Attach | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2::Attach
helpviewer_keywords: IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 111895b73ee9685b9608be9812452d04d84cd48c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Этот метод сообщает процесс, что сеанс теперь отлаживаемого процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pSession`  
 [in] Значение, уникально идентифицирующий сеанс, присоединение к этому процессу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Переданный интерфейс `pSession` следует рассматривать только в качестве файла cookie, значение, однозначно определяющее диспетчера сеанса отладки, присоединение к этому процессу; ни один из методов в интерфейсе предоставленного работают.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
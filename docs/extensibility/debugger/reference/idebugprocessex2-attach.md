---
title: IDebugProcessEx2::Attach | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c19f5f3c8beedf4a7de5dc5631ed1d795a125d56
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114256"
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
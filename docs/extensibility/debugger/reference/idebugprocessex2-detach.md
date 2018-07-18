---
title: IDebugProcessEx2::Detach | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0423ae28bfee6e9acf10e2a9682e58a973c37d70
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114269"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Этот метод сообщает процесс, что сеанс больше не является отладка процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pSession`  
 [in] Значение, уникально идентифицирующий сеанс отсоединение от этого процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Переданный интерфейс `pSession` является следует рассматривать только в качестве файла cookie, значение, однозначно определяющее диспетчера сеанса отладки, который изначально подключен этот процесс; ни один из методов в интерфейсе предоставленного работают.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
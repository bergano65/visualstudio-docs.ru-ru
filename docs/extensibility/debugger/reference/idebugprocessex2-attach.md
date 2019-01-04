---
title: IDebugProcessEx2::Attach | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 3bef8e8016d89c2a7a4c98e9f486358fa8ba108a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905115"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Этот метод сообщает процесс, что сеанс теперь является отладка процесса.  
  
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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Переданный интерфейс `pSession` следует рассматривать только как файл cookie, значение, однозначно определяющий диспетчер отладки сеансов, присоединение к этому процессу; ни один из методов предоставленного интерфейса являются рабочими.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
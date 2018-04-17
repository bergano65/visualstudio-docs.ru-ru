---
title: IDebugProgramEx2::Attach | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c58f576a0126472ad60ceeb5fc5289b668bd54dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Сеанс присоединения к программе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , представляющий модуль вложенного отладки отправка событий в функции обратного вызова.  
  
 `dwReason`  
 [in] Значение из [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) перечисление, описывающее причину операции присоединения.  
  
 `pSession`  
 [in] Значение, уникально идентифицирующий сеанс, присоединение к программе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Этот метод должен возвращать `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` Если программа уже присоединен.  
  
## <a name="remarks"></a>Примечания  
 Порт, в которой находится программа может использовать значение в `pSession` для определения, какой сеанс пытается выполнить присоединение к программе. Например если порт допускает только один отладку для присоединения к процессу одновременно, порт можно определить, если сеанс уже присоединен к другие программы, в процессе.  
  
> [!NOTE]
>  Переданный интерфейс `pSession` следует рассматривать только в качестве файла cookie, значение, однозначно определяющее диспетчера сеанса отладки, присоединение к этой программе; ни один из методов в интерфейсе предоставленного работают.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
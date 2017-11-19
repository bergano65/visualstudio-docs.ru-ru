---
title: "IDebugProgramEx2::Attach | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEx2::Attach
helpviewer_keywords: IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8d025d4e788ac63ab0c75429e08c48215b9c902
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
---
title: IDebugDisassemblyStream2::GetCodeLocationId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b92bb6dbb25dc70032c04041c49164fc8f963bc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988539"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Возвращает идентификатор расположения кода для контекста кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pCodeContext`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) объект для преобразования в идентификатор.  
  
 `puCodeLocationId`  
 [out] Возвращает идентификатор расположение кода. См. заметки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_CODE_CONTEXT_OUT_OF_SCOPE` Если контекст кода является допустимым, но за пределами области действия.  
  
## <a name="remarks"></a>Примечания  
 Идентификатор расположения кода относится только к модуль отладки (DE), поддерживающий дизассемблированного кода. Этот идентификатор расположения является внутренним классом DE для отслеживания позиции в коде и обычно является адрес или смещение некоторого типа. Единственным требованием является контекст кода из одного места меньше, чем контекст кода из другого места, то соответствующий идентификатор расположения кода первого контекста кода также должен быть меньше, чем идентификатора расположения кода второй контекста кода.  
  
 Чтобы получить контекст кода идентификатора в расположение кода, вызовите [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
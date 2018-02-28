---
title: "IDebugThread2::SetNextStatement | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6c70c1c1d3e525ccc676554d3b40df224423e313
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Задает контекст данного кода текущего указателя инструкций.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pStackFrame`  
 Зарезервировано для будущего использования; присвоено значение null.  
  
 `pCodeContext`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , описывающий расположение кода будет выполнена и его контекста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Ниже приведены другие возможные значения.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Следующий оператор не может быть в кадре стека глубже на кадра стека.|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Следующий оператор не связан с любыми кадрами стека.|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Некоторые отладчики не удается задать следующий оператор после исключения.|  
  
## <a name="remarks"></a>Примечания  
 Указатель инструкции указывает Далее инструкцию или инструкции для выполнения. Этот метод используется попытки строка исходного кода или для принудительного выполнения продолжают выполняться в другой функции, например.  
  
## <a name="see-also"></a>См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
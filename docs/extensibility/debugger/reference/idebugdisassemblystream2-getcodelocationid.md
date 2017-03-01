---
title: "IDebugDisassemblyStream2::GetCodeLocationId | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b64ad6cc146c2e2457cf9c39d5ce2c5d8f78cf65
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Возвращает идентификатор расположение кода для контекста определенного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```c#  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pCodeContext`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) преобразуемого с идентификатором объекта.  
  
 `puCodeLocationId`  
 [out] Возвращает идентификатор расположение кода. См. заметки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает `E_CODE_CONTEXT_OUT_OF_SCOPE` Если контекст кода является допустимым, но за пределами области.  
  
## <a name="remarks"></a>Примечания  
 Идентификатор расположение кода относится только к ядра отладки (DE), поддерживающий дизассемблированного кода. Этот идентификатор расположение используется внутренне DE для отслеживания позиции в коде и обычно является адрес или смещение некоторого типа. Единственное требование: Если контекст кода из одного места меньше, чем контекст кода из другого места, то соответствующий идентификатор расположение кода первого контекста кода также должна быть меньше, чем идентификатор расположение кода второй контекст кода.  
  
 Чтобы получить контекст кода идентификатора в расположение кода, вызовите [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)

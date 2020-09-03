---
title: 'IDebugDisassemblyStream2:: Жеткоделокатионид | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebb2280f814985e2352413921a00268d96761b7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196226"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает идентификатор расположения кода для определенного контекста кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Объект [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) для преобразования в идентификатор.  
  
 `puCodeLocationId`  
 заполняет Возвращает идентификатор расположения кода. См. заметки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает значение, `E_CODE_CONTEXT_OUT_OF_SCOPE` Если контекст кода является допустимым, но находится за пределами области.  
  
## <a name="remarks"></a>Remarks  
 Идентификатор расположения кода зависит от модуля отладки (DE), поддерживающего дизассемблирование. Этот идентификатор расположения используется для внутренних целей DE для трассировки положений в коде и обычно является адресом или смещением какого-либо типа. Единственное требование заключается в том, что если контекст кода одного места меньше, чем контекст кода другого расположения, соответствующий идентификатор местоположения кода первого контекста кода также должен быть меньше, чем идентификатор расположения кода второго контекста кода.  
  
 Чтобы получить контекст кода для идентификатора расположения кода, вызовите метод [жеткодеконтекст](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)

---
title: IDebugDisassemblyStream2::GetCodeLocationId | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2e388219d00c2fa3be9d3be61667328c6a189f0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571754"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugDisassemblyStream2::GetCodeLocationId](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid).  
  
Возвращает идентификатор расположения кода для контекста кода.  
  
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


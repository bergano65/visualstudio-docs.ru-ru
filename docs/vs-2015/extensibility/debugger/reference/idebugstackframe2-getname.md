---
title: IDebugStackFrame2::GetName | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetName
helpviewer_keywords:
- IDebugStackFrame2::GetName
ms.assetid: 069d4f96-363f-404e-9c89-5318c4c9821b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d2ee8b174c69a9416eb7f6889f6ac112abf5a7c0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993157"
---
# <a name="idebugstackframe2getname"></a>IDebugStackFrame2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает имя кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName (   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrName`  
 [out] Возвращает имя кадра стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Как правило, имя кадр стека — имя выполняемого метода.  
  
## <a name="see-also"></a>См. также  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)

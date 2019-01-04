---
title: IDebugProgram2::EnumCodePaths | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e0aef8d28fcbe0a416d70d9ddbac0157f246e83c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53884754"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Возвращает список путей для заданной позиции в исходном файле.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```csharp  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszHint`  
 [in] Слово под курсором в **источника** или **Дизассемблированный код** представления в интегрированной среде разработки.  
  
 `pStart`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) объект, представляющий текущий контекст кода.  
  
 `pFrame`  
 [in] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) объект, представляющий кадр стека связанный с текущей точкой останова.  
  
 `fSource`  
 [in] Ненулевое значение (`TRUE`) if в **источника** представления, или нуль (`FALSE`) if в **Дизассемблированный код** представления.  
  
 `ppEnum`  
 [out] Возвращает [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) объект, содержащий список путей кода.  
  
 `ppSafety`  
 [out] Возвращает [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) объект, представляющий контекст дополнительный код в качестве точки останова в случае, если выбранный путь кода пропускается. Это может произойти в случае сокращенное логическое выражение, например.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Путь код описывает имя метода или функции, который был вызван для получения к текущей точке выполнения программы. Список путей кода представляет стек вызовов.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
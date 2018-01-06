---
title: "IDebugProgram2::EnumCodePaths | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::EnumCodePaths
helpviewer_keywords: IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c9e87e3435f5902e277a2c80c68ab2dab891bd38
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Извлекает список путей для заданной позиции в файле исходного кода.  
  
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
 [in] Слова под курсором в **источника** или **Дизассемблирование** представления в Интегрированной среде разработки.  
  
 `pStart`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) объект, представляющий текущий контекст кода.  
  
 `pFrame`  
 [in] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) объект, представляющий кадр стека связанные с текущей точки останова.  
  
 `fSource`  
 [in] Ненулевое значение (`TRUE`) в случае, если **источника** представление, или нуль (`FALSE`) в случае, если **Дизассемблированный код** представления.  
  
 `ppEnum`  
 [out] Возвращает [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) объекта, содержащего список путей кода.  
  
 `ppSafety`  
 [out] Возвращает [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) объект, представляющий контекст дополнительный код в качестве точки останова в случае, если выбранный путь кода пропускается. Это может произойти в случае сокращенное логическое выражение, например.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Пути к коду описывается имя метода или функции, которая была вызвана для получения в текущий момент в процессе выполнения программы. Список путей кода представляет стека вызовов.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
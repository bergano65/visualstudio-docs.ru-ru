---
title: "BSTR_ARRAY | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BSTR_ARRAY
helpviewer_keywords: BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32ef5a93cc5051e2431305dd5181908e9cb7b153
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="bstrarray"></a>BSTR_ARRAY
Структура, описывающая массив строк.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct tagBSTR_ARRAY {  
   DWORD dwCount;  
   BSTR* Members;  
} BSTR_ARRAY;  
```  
  
```csharp  
struct BSTR_ARRAY {  
   DWORD    dwCount;  
   string[] Members;  
}  
```  
  
## <a name="terms"></a>Термины  
 dwCount  
 Число строк в `Members` массива.  
  
 Члены  
 Массив строк.  
  
## <a name="remarks"></a>Примечания  
 Эта структура возвращается из [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) метод.  
  
 [C++] Каждой отдельной строки должны быть высвобождены с `SysFreeString`и `Members` массива должны быть освобождены вызовом `CoTaskMemFree`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
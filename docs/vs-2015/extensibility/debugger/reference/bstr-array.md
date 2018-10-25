---
title: BSTR_ARRAY | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 095297424b456e5a9ad903b1816f58e9849c4433
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913388"
---
# <a name="bstrarray"></a>BSTR_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Структура, описывающая массив строк.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
 Участники  
 Массив строк.  
  
## <a name="remarks"></a>Примечания  
 Эта структура возвращается из [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) метод.  
  
 [C++] Каждой отдельной строки должны быть высвобождены с помощью `SysFreeString`и `Members` массива должны быть высвобождены с `CoTaskMemFree`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)


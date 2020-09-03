---
title: BSTR_ARRAY | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912537eb632768b3bcb6543dab098126ce02424f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153185"
---
# <a name="bstr_array"></a>BSTR_ARRAY
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
 двкаунт  
 Количество строк в `Members` массиве.  
  
 Элементы  
 Массив строк.  
  
## <a name="remarks"></a>Remarks  
 Эта структура возвращается методом [енумперсистедпортс](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) .  
  
 [Только C++] Каждая отдельная строка должна быть освобождена с помощью `SysFreeString` , а `Members` массив должен быть освобожден с использованием `CoTaskMemFree` .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)

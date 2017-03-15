---
title: "CONTEXT_INFO | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 11
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
ms.openlocfilehash: 9d2ecfdd70c2c299704b89de1cacec321f0ecdc1
ms.lasthandoff: 02/22/2017

---
# <a name="contextinfo"></a>CONTEXT_INFO
Эта структура описывает контекст памяти или контекст кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```c#  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>Члены  
 dwFields  
 Сочетание флагов из он [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) перечисления, которое указывает, какие поля заполняются**.**  
  
 bstrModuleUrl  
 Имя модуля, где находится контекста.  
  
 bstrFunction  
 Имя функции, где находится контекста.  
  
 posFunctionOffset  
 Объект [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) структура, которая определяет смещение строки и столбца, функции, связанные с контекстом кода.  
  
 bstrAddress  
 Адрес в коде, где находится данный контекст.  
  
 bstrAddressOffset  
 Смещение по адресу в коде, где находится данный контекст.  
  
 bstrAddressAbsolute  
 Абсолютный адрес в памяти, где находится данный контекст.  
  
## <a name="remarks"></a>Примечания  
 Эта структура возвращается из вызова [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) метод.  
  
 Обычно эта структура используется поддержки **памяти** окно отладки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

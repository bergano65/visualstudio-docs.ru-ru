---
title: CONTEXT_INFO | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4e8c1b438cd2fa2721e81f055695e5836c26d12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179939"
---
# <a name="context_info"></a>CONTEXT_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
```csharp  
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
  
## <a name="members"></a>Участники  
 двфиелдс  
 Сочетание флагов из [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) перечисление, которое указывает, какие поля заполняются<strong>.</strong>  
  
 бстрмодулеурл  
 Имя модуля, в котором находится контекст.  
  
 бстрфунктион  
 Имя функции, в которой находится контекст.  
  
 посфунктионоффсет  
 Структура [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , определяющая смещение строки и столбца функции, связанной с контекстом кода.  
  
 бстраддресс  
 Адрес в коде, где находится заданный контекст.  
  
 бстраддрессоффсет  
 Смещение адреса в коде, где находится заданный контекст.  
  
 бстраддрессабсолуте  
 Абсолютный адрес в памяти, где находится заданный контекст.  
  
## <a name="remarks"></a>Remarks  
 Эта структура возвращается из вызова метода " [info](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) ".  
  
 Типичное использование этой структуры — поддержка окна отладки **памяти** .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Сведения](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

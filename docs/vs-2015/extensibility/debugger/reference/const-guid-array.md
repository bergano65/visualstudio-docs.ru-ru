---
title: CONST_GUID_ARRAY | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 43715ca8fa8174b2b8b9509a93e98cf15ad4611c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198866"
---
# <a name="const_guid_array"></a>CONST_GUID_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Структура, содержащая список `GUID` s.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct tagCONST_GUID_ARRAY {  
   DWORD       dwCount;  
   CONST GUID* Members;  
} CONST_GUID_ARRAY;  
```  
  
```csharp  
public struct CONST_GUID_ARRAY {  
   public uint   dwCount;  
   public Guid[] Members;  
}  
```  
  
## <a name="members"></a>Участники  
 двкаунт  
 Число объектов `GUID` в `Members` массиве.  
  
 Элементы  
 Массив объектов `GUID` s.  
  
## <a name="remarks"></a>Remarks  
 Эта структура передается в метод [публишпрограм](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) и возвращается из методов [жетпровидерпроцессдата](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) и [ватчфорпровидеревентс](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md) .  
  
 Владелец экземпляра этой структуры отвечает за освобождение выделенной памяти.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [публишпрограм](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)   
 [жетпровидерпроцессдата](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

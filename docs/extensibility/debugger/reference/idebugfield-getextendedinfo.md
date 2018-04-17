---
title: IDebugField::GetExtendedInfo | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63bf182e4e8b17133fbefd4f4a19c4b8b4a458e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Этот метод возвращает расширенные сведения о поле.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidExtendedInfo`  
 [in] Выбирает возвращаемых данных. Допустимые значения:  
  
|Значение|Описание|  
|-----------|-----------------|  
|`guidConstantValue`|Значение в виде последовательности байтов.|  
|`guidConstantType`|Тип сигнатуры типа.|  
  
 `prgBuffer`  
 [out] Возвращает расширенные сведения.  
  
 `pdwLen`  
 [in, out] Возвращает размер расширенных сведений в байтах.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 В настоящее время этот метод возвращает только типа или значения константы. Вызывающий объект должен освободить буфер, возвращенный в `prgBuffer` путем вызова COM `CoTaskMemFree` функции (C++) или <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).  
  
## <a name="see-also"></a>См. также  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
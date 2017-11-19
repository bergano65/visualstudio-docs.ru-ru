---
title: "IDebugField::GetExtendedInfo | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetExtendedInfo
helpviewer_keywords: IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5b52c5634b4b34edf11ddb8a56317cc237063bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
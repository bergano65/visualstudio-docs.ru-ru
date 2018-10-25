---
title: IDebugField::GetExtendedInfo | Документация Майкрософт
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
ms.openlocfilehash: b276b2bff8e8ab5af0f007fbc5bd5dd6074c4d9d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896051"
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
 [in] Выбирает возвращаемые данные. Допустимые значения:  
  
|Значение|Описание|  
|-----------|-----------------|  
|`guidConstantValue`|Значение в виде последовательности байтов.|  
|`guidConstantType`|Тип в виде сигнатура типа.|  
  
 `prgBuffer`  
 [out] Возвращает расширенные сведения.  
  
 `pdwLen`  
 [in, out] Возвращает размер расширенных сведений, в байтах.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 В настоящее время этот метод возвращает только типа или значения константы. Вызывающий объект должен освободить буфер, возвращается в `prgBuffer` путем вызова COM `CoTaskMemFree` функции (C++) или <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).  
  
## <a name="see-also"></a>См. также  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
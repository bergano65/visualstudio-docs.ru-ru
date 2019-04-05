---
title: IDebugField::GetExtendedInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3de21bc984a36db87f8ce1567f4ff7d97212c40e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992793"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод возвращает расширенные сведения о поле.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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

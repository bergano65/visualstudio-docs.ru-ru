---
title: 'Идебугфиелд:: Жетекстендединфо | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547563"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод получает расширенные сведения о поле.  
  
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
 окне Выбирает возвращаемые данные. Допустимые значения:  
  
|Значение|Описание|  
|-----------|-----------------|  
|`guidConstantValue`|Значение в виде последовательности байтов.|  
|`guidConstantType`|Тип в виде сигнатуры типа.|  
  
 `prgBuffer`  
 заполняет Возвращает расширенные сведения.  
  
 `pdwLen`  
 [вход, выход] Возвращает размер расширенной информации в байтах.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 В настоящее время этот метод возвращает только тип или значение константы. Вызывающий объект должен освободить буфер, возвращенный в `prgBuffer` , вызвав `CoTaskMemFree` функцию com (C++) или <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).  
  
## <a name="see-also"></a>См. также:  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

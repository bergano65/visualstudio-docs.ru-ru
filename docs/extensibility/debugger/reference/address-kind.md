---
title: ADDRESS_KIND | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65e4c103884da28bedfd221e26b159e9e8f98e55
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867427"
---
# <a name="addresskind"></a>ADDRESS_KIND
Указывает типы адресов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```csharp  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## <a name="terms"></a>Термины  
 ADDRESS_KIND_NATIVE  
 Собственный адрес, представленный [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) структуры.  
  
 ADDRESS_KIND_UNMANAGED_THIS_RELATIVE  
 Неуправляемый адрес относительно `this` (`Me` в Visual Basic) указатель и представленный [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) структуры.  
  
 ADDRESS_KIND_UNMANAGED_PHYSICAL  
 Неуправляемый физический адрес, представленный [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) структуры.  
  
 ADDRESS_KIND_METHOD  
 Метод класса, представленного [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) структуры.  
  
 ADDRESS_KIND_FIELD  
 Поле класса, представленного [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) структуры.  
  
 ADDRESS_KIND_LOCAL  
 Адрес для локальной переменной, а также представлен [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) структуры.  
  
 ADDRESS_KIND_PARAM  
 Параметр метода или функции, представленной [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) структуры.  
  
 ADDRESS_KIND_ARRAYELEM  
 Элемент массива, представленный [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) структуры.  
  
 ADDRESS_KIND_RETVAL  
 Возвращаемое значение, представленное [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) структуры.  
  
## <a name="remarks"></a>Примечания  
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) возвращает [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структуры, который содержит объединение множества возможных структур [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуры. `dwKind` Поле `DEBUG_ADDRESS_UNION` структуры содержит `ADDRESS_KIND` значение и описывается, как интерпретировать поле объединения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
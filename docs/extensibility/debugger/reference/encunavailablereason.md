---
title: EncUnavailableReason | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dcf705015925145b790b14a44007fed8d8fad3b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Представляет по причинам, **изменить и продолжить** недоступна.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 ENCUN_NONE  
 Нет особых причин, почему изменить и продолжить не доступен.  
  
 ENCUN_INTEROP  
 Изменить и продолжить доступен не во время вызова взаимодействия.  
  
 ENCUN_SQLCLR  
 Изменить и продолжить доступен не во время вызова процедуры SQL, который использует Common Language Runtime (CLR).  
  
 ENCUN_MINIDUMP  
 Изменить и продолжить доступен не во время обработки мини-дампа.  
  
 ENCUN_EMBEDDED  
 Изменить и продолжить недоступен, при обработке внедренный код.  
  
 ENCUN_ATTACH  
 Изменить и продолжить недоступно, так как сеанс был прикреплен к, не запускается в отладчике.  
  
 ENCUN_WIN64  
 Изменить и продолжить доступен не во время обработки 64-разрядном коде Windows.  
  
## <a name="remarks"></a>Примечания  
 Это перечисление предназначено для внутреннего использования только с [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]. [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) и [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) методы, реализуемый поставщиком пользовательский порт всегда должны возвращать `E_NOTIMPL`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.idl  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
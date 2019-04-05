---
title: EncUnavailableReason | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ebdc5518579223a0081f30a0affd3a45e91604e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989658"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!` Представляет по причинам, **изменить и продолжить** недоступна.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
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
 Нет особых причин, почему изменить и продолжить недоступен.  
  
 ENCUN_INTEROP  
 Изменить и продолжить недоступен во время вызова взаимодействия.  
  
 ENCUN_SQLCLR  
 Изменить и продолжить недоступен во время вызова процедуры SQL, которая использует Common Language Runtime (CLR).  
  
 ENCUN_MINIDUMP  
 Изменить и продолжить недоступен во время обработки мини-дампа.  
  
 ENCUN_EMBEDDED  
 Изменить и продолжить недоступна, при обработке внедренный код.  
  
 ENCUN_ATTACH  
 Изменить и продолжить недоступно, так как сеанс был подключен к, не запускается отладчиком,.  
  
 ENCUN_WIN64  
 Изменить и продолжить при обработке 64-разрядный код Windows недоступна.  
  
## <a name="remarks"></a>Примечания  
 Это перечисление предназначено для внутреннего использования только по [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) и [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) всегда должны возвращать методы как реализованный поставщика пользовательского порта `E_NOTIMPL`.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.idl  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)

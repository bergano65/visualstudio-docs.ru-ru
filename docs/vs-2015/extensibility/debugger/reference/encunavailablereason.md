---
title: Енкунаваилаблереасон | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198773"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!` Представляет причины недоступности **"изменить и продолжить"** .  
  
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
 Нет никакой конкретной причины, почему "изменить и продолжить" недоступен.  
  
 ENCUN_INTEROP  
 Операции "изменить и продолжить" недоступны во время вызова взаимодействия.  
  
 ENCUN_SQLCLR  
 Операция "изменить и продолжить" недоступна во время вызова процедуры SQL, использующей среду CLR.  
  
 ENCUN_MINIDUMP  
 Операции "изменить и продолжить" недоступны при обработке мини-дампа.  
  
 ENCUN_EMBEDDED  
 Операции "изменить и продолжить" недоступны при обработке внедренного кода.  
  
 ENCUN_ATTACH  
 Параметр "изменить и продолжить" недоступен, так как сеанс был подключен к, а не запущен с помощью отладчика.  
  
 ENCUN_WIN64  
 Операции "изменить и продолжить" недоступны при обработке 64-разрядного кода Windows.  
  
## <a name="remarks"></a>Remarks  
 Это перечисление предназначено только для внутреннего использования [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] . Методы [жетенкаваилаблестате](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) и [дисаблинк](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) , реализованные пользовательским поставщиком портов, всегда должны возвращать значение `E_NOTIMPL` .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. idl  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [дисаблинк](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)

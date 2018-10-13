---
title: EncUnavailableReason | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0c203865e8ffe7ab3d94cc9c2e4f4bd356d2a2dc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295378"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!` Представляет по причинам, **изменить и продолжить** недоступна.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Заголовок: msdbg.idl  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)


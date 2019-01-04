---
title: PORT_SUPPLIER_DESCRIPTION_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- PORT_SUPPLIER_DESCRIPTION_FLAGS enumeration
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0db1d83a9e4f41ae349da121300d4f45284836ca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893183"
---
# <a name="portsupplierdescriptionflags"></a>PORT_SUPPLIER_DESCRIPTION_FLAGS
Определяет метаданные, которые могут быть получены о поставщика порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS  
{  
   PSDFLAG_SHOW_WARNING_ICON = 0x1  
};  
typedef DWORD PORT_SUPPLIER_DESCRIPTION_FLAGS;  
```  
  
```csharp  
public enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS  
{  
   PSDFLAG_SHOW_WARNING_ICON = 0x1  
};  
```  
  
## <a name="terms"></a>Термины  
 PSDFLAG_SHOW_WARNING_ICON  
 Если флажок установлен, в пользовательском Интерфейсе отображается значок предупреждения.  
  
## <a name="remarks"></a>Примечания  
 Это перечисление возвращается [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)
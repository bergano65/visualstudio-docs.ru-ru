---
title: CANSTOP_REASON | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4129839094b7f5cf9907f6b92fa11fe1847f5806
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938816"
---
# <a name="canstopreason"></a>CANSTOP_REASON
Используется для определения того, если программы можно остановить выполнение после достижения определенной точке выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>Участники  
 CANSTOP_ENTRYPOINT  
 Определяет точку входа данной программы.  
  
 CANSTOP_STEPIN  
 Указывает, шаг с заходом в функцию.  
  
## <a name="remarks"></a>Примечания  
 Передается в качестве аргумента для [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) метод подтверждения с сеанса отладки Manager (SDM), если необходимо остановить после достижения точки входа программы или шаг с заходом в функции или метода.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
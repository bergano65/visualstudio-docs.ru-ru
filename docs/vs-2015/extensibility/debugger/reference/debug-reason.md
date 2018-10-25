---
title: DEBUG_REASON | Документация Майкрософт
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
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b94b1503e5f12cbcb7aa120fd816302d9a305b5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844595"
---
# <a name="debugreason"></a>DEBUG_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает, почему был запущен процесс для отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 DEBUG_REASON_ERROR  
 Произошла общая ошибка (используется как условие по умолчанию при ни с одним другим причинам, по размеру).  
  
 DEBUG_REASON_USER_LAUNCHED  
 Процесс был запущен по запросу пользователя.  
  
 DEBUG_REASON_USER_ATTACHED  
 Уже выполняемым процессам был подключен к этим пользователем.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 Процесс автоматически присоединяется к, если оно было запущено.  
  
 DEBUG_REASON_CAUSALITY  
 Процесс был запущен из-за *Just-In-Time* событие отладки (JIT).  
  
## <a name="remarks"></a>Примечания  
 Возвращаемые [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)


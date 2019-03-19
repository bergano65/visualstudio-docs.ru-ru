---
title: Интерфейс IJsDebugBreakPoint | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 791c8488-21e7-46be-b1b4-fe74117cf200
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14823baeb999ad24aabef9b2b55b59a7b5d08c71
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157728"
---
# <a name="ijsdebugbreakpoint-interface"></a>Интерфейс IJsDebugBreakPoint
Представляет точку останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IJsDebugBreakPoint : public IUnknown;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[Метод IJsDebugBreakPoint::Delete](../../winscript/reference/ijsdebugbreakpoint-delete-method.md)|Удаляет точку останова.|  
|[Метод IJsDebugBreakPoint::Disable](../../winscript/reference/ijsdebugbreakpoint-disable-method.md)|Отключает точку останова.|  
|[Метод IJsDebugBreakPoint::Enable](../../winscript/reference/ijsdebugbreakpoint-enable-method.md)|Включает точку останова.|  
|[Метод IJsDebugBreakPoint::GetDocumentPosition](../../winscript/reference/ijsdebugbreakpoint-getdocumentposition-method.md)|Возвращает позицию инструкции, где была привязана точка останова.|  
|[Метод IJsDebugBreakPoint::IsEnabled](../../winscript/reference/ijsdebugbreakpoint-isenabled-method.md)|Определяет, включена ли точка останова.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)
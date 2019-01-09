---
title: Интерфейс IJsDebugProcess | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecdec77a8bcb3c1fb8a1dc64c63b363b4f001fde
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086662"
---
# <a name="ijsdebugprocess-interface"></a>Интерфейс IJsDebugProcess
Содержит процедуры для проверки и контроля в целевом процессе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[Метод IJsDebugProcess::CreateBreakPoint](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Задает точку останова в позицию указанного документа.|  
|[Метод IJsDebugProcess::CreateStackWalker](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Фабричный метод для средства обхода стека.|  
|[Метод IJsDebugProcess::PerformAsyncBreak](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Помещает обработчик скриптов в режиме приостановки выполнения вызывает его на прерывание в следующей инструкции скрипта.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)
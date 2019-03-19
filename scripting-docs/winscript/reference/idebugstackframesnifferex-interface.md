---
title: Интерфейс IDebugStackFrameSnifferEx | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc6e892c00a2d86e784857f08772550897e1ec4e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157190"
---
# <a name="idebugstackframesnifferex-interface"></a>Интерфейс IDebugStackFrameSnifferEx
Предоставляет способ для перечисления логических кадров стека известные компонентом. Этот интерфейс обычно реализуется обработчиков сценариев. Диспетчер отладки процесса использует этот интерфейс, чтобы найти все кадры стека, связанные с данного потока.  
  
> [!NOTE]
>  Этот интерфейс вызывается из потока интерес. В реализации интерфейса необходимо определить текущий поток и возврата перечислителя, соответствующий.  
  
 Помимо методов, наследуемых от `IDebugStackFrameSniffer`, `IDebugStackFrameSnifferEx` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Возвращает перечислитель для кадров стека текущего потока.|
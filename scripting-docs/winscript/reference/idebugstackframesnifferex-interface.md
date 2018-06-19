---
title: Интерфейс IDebugStackFrameSnifferEx | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 56d6e63c41db274634b2593989800ea0392b93a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726764"
---
# <a name="idebugstackframesnifferex-interface"></a>Интерфейс IDebugStackFrameSnifferEx
Предоставляет способ для перечисления логических стека, известные компонентом. Обработчики скриптов обычно реализуют этот интерфейс. Диспетчер отладки процесса использует этот интерфейс, чтобы найти все кадры стека, связанные с данного потока.  
  
> [!NOTE]
>  Этот интерфейс вызывается из потока, представляющие интерес. Реализации интерфейса необходимо указать текущий поток и возвращать соответствующий перечислитель.  
  
 Помимо методов, наследуемых от `IDebugStackFrameSniffer`, `IDebugStackFrameSnifferEx` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Возвращает перечислитель кадров стека текущего потока.|
---
title: Интерфейс IDebugStackFrameSniffer | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41fff384bc9075d94fcfa84d94350fec72ebc64a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348884"
---
# <a name="idebugstackframesniffer-interface"></a>Интерфейс IDebugStackFrameSniffer
Предоставляет способ для перечисления логических кадров стека известные компонентом. Этот интерфейс обычно реализуется обработчиков сценариев. Диспетчер отладки процесса использует этот интерфейс, чтобы найти все кадры стека, связанные с данного потока.  
  
> [!NOTE]
>  Отладчик вызывает этот интерфейс из потока, представляющие интерес. Обработчик скриптов должна определить текущий поток и возвращать соответствующий перечислитель.  
  
## <a name="methods"></a>Методы  
 Помимо методов, наследуемых от `IUnknown`, `IDebugStackFrameSniffer` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Возвращает перечислитель для кадров стека текущего потока.|
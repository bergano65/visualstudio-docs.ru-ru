---
title: Интерфейс IDebugStackFrameSniffer | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 5c9181b5013a9584a2a686ed0e499698be0b62b9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432260"
---
# <a name="idebugstackframesniffer-interface"></a>Интерфейс IDebugStackFrameSniffer
Предоставляет способ для перечисления логических кадров стека известные компонентом. Этот интерфейс обычно реализуется обработчиков сценариев. Диспетчер отладки процесса использует этот интерфейс, чтобы найти все кадры стека, связанные с данного потока.  
  
> [!NOTE]
> Отладчик вызывает этот интерфейс из потока, представляющие интерес. Обработчик скриптов должна определить текущий поток и возвращать соответствующий перечислитель.  
  
## <a name="methods"></a>Методы  
 Помимо методов, наследуемых от `IUnknown`, `IDebugStackFrameSniffer` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Возвращает перечислитель для кадров стека текущего потока.|
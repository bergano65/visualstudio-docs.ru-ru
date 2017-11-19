---
title: "Интерфейс IDebugStackFrameSniffer | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250c104d24f27900a6ff0eb8e8f72644f820bf5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesniffer-interface"></a>Интерфейс IDebugStackFrameSniffer
Предоставляет способ для перечисления логических стека, известные компонентом. Обработчики скриптов обычно реализуют этот интерфейс. Диспетчер отладки процесса использует этот интерфейс, чтобы найти все кадры стека, связанные с данного потока.  
  
> [!NOTE]
>  Отладчик вызывает этот интерфейс из потока, представляющие интерес. Обработчик скриптов необходимо указать текущий поток и возвращать соответствующий перечислитель.  
  
## <a name="methods"></a>Методы  
 Помимо методов, наследуемых от `IUnknown`, `IDebugStackFrameSniffer` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Возвращает перечислитель кадров стека текущего потока.|
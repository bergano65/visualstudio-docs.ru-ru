---
title: IDebugApplicationThreadEvents110::OnSuspendForBreakPoint | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
ms.assetid: 224245ac-2aa2-43ae-97ed-493afc3d0122
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9e39af9784b139e935c271fca6db565136352cf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440425"
---
# <a name="idebugapplicationthreadevents110onsuspendforbreakpoint"></a>IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
Определяет, полностью приостановил для точки останова и еще не возобновлено обычное выполнение потока.  
  
> [!IMPORTANT]
> [Интерфейс IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md) является реализуется PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT OnSuspendForBreakPoint( void );  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не имеет параметров.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md)
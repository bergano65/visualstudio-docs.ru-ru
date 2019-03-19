---
title: IDebugApplicationThreadEvents110::OnResumeFromBreakPoint | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnResumeFromBreakPoint
ms.assetid: 4c97b9a3-fced-487e-a81c-e3f8f2cb7927
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b681a9c89a2b7d48864e7ed3fc48460c64d2878
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160606"
---
# <a name="idebugapplicationthreadevents110onresumefrombreakpoint"></a>IDebugApplicationThreadEvents110::OnResumeFromBreakPoint
Поток возобновляет работу из точки останова и будут активными еще раз.  
  
> [!IMPORTANT]
>  [Интерфейс IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md) является реализуется PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT OnResumeFromBreakPoint( void );  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не имеет параметров.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md)
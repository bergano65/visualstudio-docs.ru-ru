---
title: 'IRemoteDebugApplication110:: Жетмаинсреад | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff99c43f633da8454eb5fa32463886877e06ed72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574121"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Возвращает основной поток для узлов, вызывающих [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), в противном случае ВОЗВРАЩАЕТ значение E_FAIL.  
  
> [!IMPORTANT]
> [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) реализуется с помощью PDM v 11.0 и более поздних версий. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppThread`  
 заполняет Основной [интерфейс иремотедебугаппликатионсреад](../../winscript/reference/iremotedebugapplicationthread-interface.md).  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)  
 [Интерфейс IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)
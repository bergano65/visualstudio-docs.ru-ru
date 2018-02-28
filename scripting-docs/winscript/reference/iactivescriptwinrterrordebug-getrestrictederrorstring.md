---
title: "IActiveScriptWinRTErrorDebug::GetRestrictedErrorString | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
ms.assetid: d901e049-fb1b-4101-a04a-1395d657f1cf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ade51ae9852519d6a059193aacbfdde49ae82d19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptwinrterrordebuggetrestrictederrorstring"></a>IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
Возвращает среды выполнения Windows только строка ошибки, если он доступен.  
  
> [!IMPORTANT]
>  [Iactivescriptwinrterrordebug — интерфейс](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) — реализованный PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetRestrictedErrorString([out] BSTR * errorString);   
```  
  
#### <a name="parameters"></a>Параметры  
 `errorString`  
 [out] Строка только ошибки.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)
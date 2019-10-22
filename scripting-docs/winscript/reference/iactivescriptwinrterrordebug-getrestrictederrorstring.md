---
title: 'Иактивескриптвинртеррордебуг:: Жетрестриктедеррорстринг | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
ms.assetid: d901e049-fb1b-4101-a04a-1395d657f1cf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 498d929fb06eea1d6717bfdecb09107bbdaafd98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577906"
---
# <a name="iactivescriptwinrterrordebuggetrestrictederrorstring"></a>IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
Возвращает среда выполнения Windows строку с ограниченным доступом, если она доступна.  
  
> [!IMPORTANT]
> [Интерфейс иактивескриптвинртеррордебуг](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) реализуется с помощью PDM v 11.0 и более поздних версий. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetRestrictedErrorString([out] BSTR * errorString);   
```  
  
#### <a name="parameters"></a>Параметры  
 `errorString`  
 заполняет Ограниченная строка ошибки.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)
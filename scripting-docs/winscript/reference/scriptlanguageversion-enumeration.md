---
title: Перечисление SCRIPTLANGUAGEVERSION | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cee2966b326ca7b4c258ffdb85b6fa71d90992
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734074"
---
# <a name="scriptlanguageversion-enumeration"></a>Перечисление SCRIPTLANGUAGEVERSION
Указывает возможные сценарии версий.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Значения перечисления  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Версия по умолчанию. Целочисленное значение — 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Скрипты Windows версии 5.7. Целочисленное значение-1.|  
|SCRIPTLANGUAGEVERSION_5_8|Версия 5.8 сценариев Windows. Целочисленное значение — 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Максимальная версия. Целочисленное значение — 255.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)
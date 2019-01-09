---
title: Перечисление SCRIPTTRACEINFO | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 866f507b4d107c8f395be6588a85f67ea6bb45c9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086753"
---
# <a name="scripttraceinfo-enumeration"></a>Перечисление SCRIPTTRACEINFO
Представляет событие скрипта, отслеживаемого. Используется в [метод IActiveScriptSiteTraceInfo::SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>Значения перечисления  
  
|||  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|Начало сценария.|  
|SCRIPTTRACEINFO_SCRIPTEND|Конец скрипта.|  
|SCRIPTTRACEINFO_COMCALLSTART|Начало вызова COM.|  
|SCRIPTTRACEINFO_COMCALLEND|Конец вызова COM.|  
|SCRIPTTRACEINFO_CREATEOBJSTART|Начало создания объекта.|  
|SCRIPTTRACEINFO_CREATEOBJEND|Конец создания объекта.|  
|SCRIPTTRACEINFO_GETOBJSTART|Начало вызова GetObject.|  
|SCRIPTTRACEINFO_GETOBJEND|Конец вызова GetObject.|
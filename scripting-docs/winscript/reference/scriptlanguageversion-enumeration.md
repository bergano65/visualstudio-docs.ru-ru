---
title: Перечисление СКРИПТЛАНГУАЖЕВЕРСИОН | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 802a9f31cc7e3497c5e5fc54395d988552f75e84
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574366"
---
# <a name="scriptlanguageversion-enumeration"></a>Перечисление SCRIPTLANGUAGEVERSION
Указывает возможные версии скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Значения перечисления  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Версия по умолчанию. Целочисленное значение равно 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows Scripting версии 5,7. Целочисленное значение равно 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows Scripting версии 5,8. Целочисленное значение равно 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Максимальная версия. Целочисленное значение равно 255.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)
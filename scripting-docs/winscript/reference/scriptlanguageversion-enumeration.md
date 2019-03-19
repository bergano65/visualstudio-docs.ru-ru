---
title: Перечисление SCRIPTLANGUAGEVERSION | Документация Майкрософт
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
ms.openlocfilehash: 6aab63989d1ae02f7c75fc9c20a14d59e8a05078
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144515"
---
# <a name="scriptlanguageversion-enumeration"></a>Перечисление SCRIPTLANGUAGEVERSION
Задает возможные сценарии версии.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Значения перечисления  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Версия по умолчанию. Целочисленное значение равно 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows Scripting версии 5.7. Целочисленное значение-1.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows Scripting версии 5.8. Целочисленное значение равно 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Максимальная версия. Целочисленное значение равно 255.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)
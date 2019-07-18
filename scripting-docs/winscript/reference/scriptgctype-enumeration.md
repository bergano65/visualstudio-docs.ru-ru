---
title: Перечисление SCRIPTGCTYPE | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a5de3ea949203ad7a6dca0ea777fdbc9514ba6d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840243"
---
# <a name="scriptgctype-enumeration"></a>Перечисление SCRIPTGCTYPE
Тип, для выполнения сборки мусора. Используется в [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>Значения перечисления  
  
|||  
|-|-|  
|SCRIPTGCTYPE_NORMAL|У обычной сборки мусора. Целочисленное значение равно 0.|  
|SCRIPTGCTYPE_EXHAUSTIVE|Выполните сбор мусора является исчерпывающим. Целочисленное значение-1.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)
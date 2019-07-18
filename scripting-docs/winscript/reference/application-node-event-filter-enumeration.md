---
title: Перечисление APPLICATION_NODE_EVENT_FILTER | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- APPLICATION_NODE_EVENT_FILTER Constants
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c1727c8d1526199d179fe137c9bf899959bc2ba
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422207"
---
# <a name="applicationnodeeventfilter-enumeration"></a>Перечисление APPLICATION_NODE_EVENT_FILTER
Указывает типы узлов, которые следует исключить при фильтрации документов кода. Используется в [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) и [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> Эти константы реализованы в PDM v10.0 и больше. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {    FILTER_EXCLUDE_NOTHING = 0,    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,    FILTER_EXCLUDE_EVAL_CODE = 0x2} APPLICATION_NODE_EVENT_FILTER;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Значение|Описание|  
|------------|-----------|-----------------|  
|FILTER_EXCLUDE_NOTHING|0x00000000|Отправка всех событий.|  
|FILTER_EXCLUDE_ANONYMOUS_CODE|0x00000001|Исключайте узлы анонимного кода. Эти узлы используются средой выполнения JScript для `new Function([args,] <code>)'`.|  
|FILTER_EXCLUDE_EVAL_CODE|0x00000002|Исключайте узлы код eval. Эти узлы используются средой выполнения JScript для поддержки eval.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
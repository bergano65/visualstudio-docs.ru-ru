---
title: "Перечисление PROFILER_RELATIONSHIP_INFO | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f01ca5e001d45907af70b46b6dc362e8ae0b2044
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="profilerrelationshipinfo-enumeration"></a>Перечисление PROFILER_RELATIONSHIP_INFO
Представляет сведения об объекте в связи. Используется в [структура PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Значение|Описание|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|Объект — это число.|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|Объект является строкой.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|Объект является объектом кучи.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|Объект не внешними, то есть в куче сбора мусора.|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|Объект является BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|Объект является ПОДСТРОКОЙ.|
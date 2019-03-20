---
title: Перечисление PROFILER_RELATIONSHIP_INFO | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0aa0a94668d06f75b959de2ee933ab079feba596
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148117"
---
# <a name="profilerrelationshipinfo-enumeration"></a>Перечисление PROFILER_RELATIONSHIP_INFO
Представляет сведения об объекте в связи. Используется в [структура PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Значение|Описание|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|Объект является числом.|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|Объект является строкой.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|Объект является объектом кучи.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|Объект не внешними, то есть в куче сбора мусора.|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|Объект является BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|Объект является ПОДСТРОКОЙ.|
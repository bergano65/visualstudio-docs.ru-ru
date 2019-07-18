---
title: Структура PROFILER_PROPERTY_TYPE_SUBSTRING_INFO | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3845c872-4302-47b6-8912-7b2d7a3b3357
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 5f873cdf2ebd394e48c1513135f1acdcd700c283
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816900"
---
# <a name="profilerpropertytypesubstringinfo-structure"></a>PROFILER_PROPERTY_TYPE_SUBSTRING_INFO Structure
Представляет сведения о типе подстроки, используются в связи. Используется в [структура PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef struct _PROFILER_PROPERTY_TYPE_SUBSTRING_INFO {    UINT length;    LPCWSTR value; } PROFILER_PROPERTY_TYPE_SUBSTRING_INFO;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Тип|Описание|  
|------------|----------|-----------------|  
|длина|UINT|Объект — целое число без знака.|  
|value|LPCWSTR|Объект — LPCWSTR.|
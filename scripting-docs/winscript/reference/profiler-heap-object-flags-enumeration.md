---
title: Перечисление PROFILER_HEAP_OBJECT_FLAGS | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0f517743-cc4a-4911-add3-a43680071a1f
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 833f3d100b2529ca4f356b50cddad6b6501297ce
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097491"
---
# <a name="profilerheapobjectflags-enumeration"></a>Перечисление PROFILER_HEAP_OBJECT_FLAGS
Флаги, которые представляют основные сведения об объекте кучи. Используется в [структура PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT            = 0x00000001,    PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT               = 0x00000002,    PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED           = 0x00000004,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL              = 0x00000008,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN      = 0x00000010,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH     = 0x00000020,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE      = 0x00000040,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE      = 0x00000080,    PROFILER_HEAP_OBJECT_FLAGS_NEW_STATE_UNAVAILABLE = 0x00000100,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE        = 0x00000200,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS    = 0x00000400,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE        = 0x00000800,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE       = 0x00001000,} PROFILER_HEAP_OBJECT_FLAGS;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Значение|Описание:|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT|0x00000001|Этот объект кучи был выделен после предыдущего запроса перечисление кучи. [Тип PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md) значения можно использовать повторно, если этот объект собран.|  
|PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT|0x00000002|Этот объект кучи является корневой объект графы объектов.|  
|PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED|0x00000004|Этот объект кучи — из сайт скрипта, которая была закрыта.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL|0x00000008|Этот объект кучи была выделена вне куче сбора мусора JavaScript.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN|0x00000010|Этот объект кучи была выделена в куче для сборки мусора и реализует интерфейс IUnknown.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH|0x00000020|Этот объект кучи была выделена вне куче сбора мусора и реализует интерфейс IDISPATCH.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE|0x00000040|Размер этот объект кучи приблизительное.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE|x00000080|Этот объект кучи размер недоступен.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE|0x00000200|Объект кучи — это экземпляр среды выполнения Windows.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS|0x00000400|Объект кучи — это класс среды выполнения среды выполнения Windows.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE|0x00000800|Объект кучи — это делегат среды выполнения Windows.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE|0x00001000|Объект кучи — в пространстве имен среды выполнения Windows.|
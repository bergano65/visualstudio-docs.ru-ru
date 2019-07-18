---
title: Тип PROFILER_EXTERNAL_OBJECT_ADDRESS | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c9642a4a-f1fd-408a-9de6-e51562337bf1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b5708dfb0ad5e419f217d6d06a3c2b039d55b35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831562"
---
# <a name="profilerexternalobjectaddress-type"></a>Тип PROFILER_EXTERNAL_OBJECT_ADDRESS
Внешний объект адрес объекта, например объектом выделенный C++, который находится за пределами кучу JavaScript. Используется в [структура PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) и [структура PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef void* PROFILER_EXTERNAL_OBJECT_ADDRESS;  
```
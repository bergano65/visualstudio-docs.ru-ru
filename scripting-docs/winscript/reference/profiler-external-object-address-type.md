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
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155999"
---
# <a name="profilerexternalobjectaddress-type"></a>Тип PROFILER_EXTERNAL_OBJECT_ADDRESS
Внешний объект адрес объекта, например объектом выделенный C++, который находится за пределами кучу JavaScript. Используется в [структура PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) и [структура PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef void* PROFILER_EXTERNAL_OBJECT_ADDRESS;  
```
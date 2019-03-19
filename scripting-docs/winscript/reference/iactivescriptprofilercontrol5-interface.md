---
title: Интерфейс IActiveScriptProfilerControl5 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dacca8e8bf161b6f3a84dc216596673d5df8258c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146439"
---
# <a name="iactivescriptprofilercontrol5-interface"></a>Интерфейс IActiveScriptProfilerControl5
Предоставляет метод для перечисления над объектами кучи GC, связанный с механизмом скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## <a name="methods"></a>Методы  
 [Метод IActiveScriptProfilerControl5::EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 Возвращает интерфейс ([интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)), можно использовать для итерации объектами кучи GC в контексте связанного обработчика скриптов.
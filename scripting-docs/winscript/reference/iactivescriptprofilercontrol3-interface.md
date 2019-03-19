---
title: Интерфейс IActiveScriptProfilerControl3 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7b57dbf76eb5dd9eadb05eb5705cdffb76106b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150924"
---
# <a name="iactivescriptprofilercontrol3-interface"></a>Интерфейс IActiveScriptProfilerControl3
Предоставляет метод для перечисления над объектами кучи GC, связанный с механизмом скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## <a name="methods"></a>Методы  
 [Метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 Возвращает интерфейс ([интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)), можно использовать для итерации объектами кучи GC в контексте связанного обработчика скриптов.
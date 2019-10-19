---
title: IActiveScriptParse | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81f64352c15dce233058d49b70e35da7e2238688
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561649"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Если обработчик сценариев Windows допускает добавление скриптов необработанного текста в скрипт или позволяет оценивать текст выражения во время выполнения, он реализует интерфейс `IActiveScriptParse`. Для интерпретируемых языков сценариев, которые не имеют независимой среды разработки, например VBScript, это предоставляет альтернативный механизм (отличный от `IPersist*`) для получения кода скрипта в обработчик сценариев, а также для присоединения фрагментов скрипта к различным событиям объекта. .  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Инициализирует обработчик скриптов.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Добавляет код скриптлет в скрипт.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Анализирует заданный код скриптлет, добавляя объявления в пространство имен и вычисляя код соответствующим образом.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)
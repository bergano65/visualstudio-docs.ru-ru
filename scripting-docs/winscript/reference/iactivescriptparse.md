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
ms.openlocfilehash: a987b4be3430f2ed8b0562f41b51a94797f96dc4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009342"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Если скрипт Windows ядра позволяет необработанный текст сценарии кода для добавления в скрипт или текст выражения, вычисляемое во время выполнения, он реализует `IActiveScriptParse` интерфейс. Интерпретируемые языки сценариев, которые имеют не независимых среду разработки, таких как VBScript, это предоставляет альтернативный механизм (отличное от `IPersist*`) для получения кода сценария в обработчик сценариев и для присоединения фрагменты кода для различных объектов события.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Инициализирует обработчика скриптов.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Сценарий кода добавляет к скрипту.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Анализирует заданного сценарий кода, а объявления в пространстве имен и вычисления код соответственно.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)
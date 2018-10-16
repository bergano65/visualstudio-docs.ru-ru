---
title: IActiveScriptParse32 | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 688a89515179912c1ed3ac815f0febf50ab4db0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724404"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Если сценарий Windows engine позволяет необработанный текст сценарии кода для добавления в скрипт или текст выражения оцениваются во время выполнения, он реализует `IActiveScriptParse32` интерфейса. Интерпретируемые языки сценариев, которые имеют не независимых среду разработки, таких как VBScript, это предоставляет альтернативный механизм (отличного от `IPersist*`) для получения кода скрипта в обработчик сценариев и для присоединения фрагменты кода для различных объектов события.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Добавляет пользователи код скрипта.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Инициализирует обработчик скриптов.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Выполняет синтаксический анализ сценариев данного кода, Добавление объявления в пространство имен и их оценка код соответствующим образом.|
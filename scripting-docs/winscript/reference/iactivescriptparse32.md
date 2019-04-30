---
title: IActiveScriptParse32 | Документация Майкрософт
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
ms.openlocfilehash: 9f44239b4e423588b8455b93b87e4084a9c7d1c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009327"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Если скрипт Windows ядра позволяет необработанный текст сценарии кода для добавления в скрипт или текст выражения, вычисляемое во время выполнения, он реализует `IActiveScriptParse32` интерфейс. Интерпретируемые языки сценариев, которые имеют не независимых среду разработки, таких как VBScript, это предоставляет альтернативный механизм (отличное от `IPersist*`) для получения кода сценария в обработчик сценариев и для присоединения фрагменты кода для различных объектов события.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Сценарий кода добавляет к скрипту.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Инициализирует обработчика скриптов.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Анализирует заданного сценарий кода, а объявления в пространстве имен и вычисления код соответственно.|
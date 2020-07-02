---
title: IActiveScriptParse32 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 568feacfe75de22a330c892a44fa4f4f6fd0e3b8
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835320"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Если обработчик сценариев Windows допускает добавление в скрипт сценариев необработанного текстового кода или позволяет оценивать текст выражения во время выполнения, он реализует `IActiveScriptParse32` интерфейс. Для интерпретируемых языков сценариев, которые не имеют независимой среды разработки, например VBScript, это предоставляет альтернативный механизм (отличный от `IPersist*` ) для получения кода скрипта в обработчик скриптов и для присоединения фрагментов скрипта к различным событиям объекта.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Добавляет код скриптлет в скрипт.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Инициализирует обработчик скриптов.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Анализирует заданный код скриптлет, добавляя объявления в пространство имен и вычисляя код соответствующим образом.|
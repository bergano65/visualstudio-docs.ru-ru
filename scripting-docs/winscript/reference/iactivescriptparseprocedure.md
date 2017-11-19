---
title: "Iactivescriptparseprocedure — | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77aaa60942855a71f7d71037fbefb06462336a13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Если обработчик скриптов Windows позволяет исходный текст кода для процедуры для добавления в скрипт, он реализует `IActiveScriptParseProcedure` интерфейса. Интерпретируемые языки сценариев, которые имеют не независимых среду разработки, таких как VBScript, это предоставляет альтернативный механизм (отличного от `IActiveScriptParse` или `IPersist`*) для добавления скрипта процедуры к пространству имен.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|||  
|-|-|  
|Метод|Описание|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Выполняет синтаксический анализ кода данной процедуры и добавляет процедуру в пространство имен.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)
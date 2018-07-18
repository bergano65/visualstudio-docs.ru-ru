---
title: Интерфейс IActiveScriptParseProcedureOld | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99cff9cd4d04c5d25489b6cc4c9b9af93792dc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724424"
---
# <a name="iactivescriptparseprocedureold-interface"></a>Интерфейс IActiveScriptParseProcedureOld
Позволяет исходный текст кода для процедуры для добавления в скрипт. Интерпретируемые языки сценариев, которые не имеют независимые среду разработки, таких как VBScript, это предоставляет альтернативный механизм (отличного от `IActiveScriptParse` или `IPersist*`) для добавления скрипта процедуры пространства имен.  
  
> [!NOTE]
>  Этот интерфейс является устаревшим для `IActiveScriptParseProcedure` интерфейса.  
  
## <a name="methods"></a>Методы  
 Помимо методов, наследуемых от `IUnknown`, `IActiveScriptParseProcedureOld` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Выполняет синтаксический анализ кода данной процедуры и добавляет процедуру в пространство имен.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)
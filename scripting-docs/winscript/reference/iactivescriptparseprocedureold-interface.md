---
title: Интерфейс IActiveScriptParseProcedureOld | Документация Майкрософт
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
ms.openlocfilehash: fa7ea909680afdb65004f47e458d735e82ead929
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54350000"
---
# <a name="iactivescriptparseprocedureold-interface"></a>Интерфейс IActiveScriptParseProcedureOld
Позволяет текстом исходного кода для процедуры для добавления в скрипт. Интерпретируемые языки сценариев, у которых нет независимых среду разработки, таких как VBScript, это предоставляет альтернативный механизм (отличное от `IActiveScriptParse` или `IPersist*`) Добавление процедуры с помощью сценариев в пространстве имен.  
  
> [!NOTE]
>  Этот интерфейс устарел, вместо него используется `IActiveScriptParseProcedure` интерфейс.  
  
## <a name="methods"></a>Методы  
 Помимо методов, наследуемых от `IUnknown`, `IActiveScriptParseProcedureOld` интерфейс предоставляет следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Выполняет синтаксический анализ данного кода процедуры и добавляет процедуру в пространстве имен.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)
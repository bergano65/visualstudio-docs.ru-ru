---
title: Интерфейс IActiveScriptParseProcedureOld | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 99fa06086bfad56b266b043716e82181aa4c97d5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160632"
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
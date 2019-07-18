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
ms.openlocfilehash: 520d3f1414447abfc7c018d36853b72aefbbf15f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386170"
---
# <a name="iactivescriptparseprocedureold-interface"></a>Интерфейс IActiveScriptParseProcedureOld
Позволяет текстом исходного кода для процедуры для добавления в скрипт. Интерпретируемые языки сценариев, у которых нет независимых среду разработки, таких как VBScript, это предоставляет альтернативный механизм (отличное от `IActiveScriptParse` или `IPersist*`) Добавление процедуры с помощью сценариев в пространстве имен.  
  
> [!NOTE]
> Этот интерфейс устарел, вместо него используется `IActiveScriptParseProcedure` интерфейс.  
  
## <a name="methods"></a>Методы  
 Помимо методов, наследуемых от `IUnknown`, `IActiveScriptParseProcedureOld` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Выполняет синтаксический анализ данного кода процедуры и добавляет процедуру в пространстве имен.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)
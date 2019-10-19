---
title: IActiveScriptParseProcedure32 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 1993cbef966a4d73a2a3ed55c3317db444702232
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574877"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Если обработчик сценариев Windows допускает добавление текста исходного кода для процедур, добавляемых в скрипт, он реализует интерфейс `IActiveScriptParseProcedure32`. Для интерпретируемых языков сценариев, не имеющих независимых сред разработки, таких как VBScript, это предоставляет альтернативный механизм (отличный от `IActiveScriptParse32` или `IPersist` *) для добавления процедур скрипта в пространство имен.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|||  
|-|-|  
|Метод|Описание|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Анализирует данную процедуру кода и добавляет процедуру в пространство имен.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)
---
title: IActiveScriptParseProcedure32 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 16d432b6c150b53fdd059a48cc683d240bd1a50a
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835307"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Если обработчик сценариев Windows позволяет добавлять текст исходного кода в скрипт, он реализует `IActiveScriptParseProcedure32` интерфейс. Для интерпретируемых языков сценариев, не имеющих независимых сред разработки, таких как VBScript, это предоставляет альтернативный механизм (отличный от `IActiveScriptParse32` или `IPersist` *) для добавления процедур сценария в пространство имен.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|||  
|-|-|  
|Метод|Описание|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Анализирует данную процедуру кода и добавляет процедуру в пространство имен.|  
  
## <a name="see-also"></a>Дополнительно  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)
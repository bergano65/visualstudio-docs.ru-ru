---
title: IActiveScriptParseProcedure32 | Документы Microsoft
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
ms.openlocfilehash: 8cd253db8cb63adad093b84c4bf47df07bd66d69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645874"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Если обработчик скриптов Windows позволяет исходный текст кода для процедуры для добавления в скрипт, он реализует `IActiveScriptParseProcedure32` интерфейса. Интерпретируемые языки сценариев, которые имеют не независимых среду разработки, таких как VBScript, это предоставляет альтернативный механизм (отличного от `IActiveScriptParse32` или `IPersist`*) для добавления скрипта процедуры к пространству имен.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|||  
|-|-|  
|Метод|Описание|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Выполняет синтаксический анализ кода данной процедуры и добавляет процедуру в пространство имен.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)
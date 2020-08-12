---
title: Иактивескриптпарсепроцедуре | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3567a22eac2ad270739e62e0f0fb9914bdf4a9ec
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144575"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Если обработчик сценариев Windows позволяет добавлять текст исходного кода в скрипт, он реализует `IActiveScriptParseProcedure` интерфейс. Для интерпретируемых языков сценариев, не имеющих независимых сред разработки, таких как VBScript, это предоставляет альтернативный механизм (отличный от `IActiveScriptParse` или `IPersist` *) для добавления процедур сценария в пространство имен.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|
|-|-|
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Анализирует данную процедуру кода и добавляет процедуру в пространство имен.|  
  
## <a name="see-also"></a>См. также раздел  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)
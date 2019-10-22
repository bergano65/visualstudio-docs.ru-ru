---
title: Интерфейс Иактивескриптпарсепроцедуреолд | Документация Майкрософт
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
ms.openlocfilehash: 4558a0cab2aea9b56db2759bb80b1287cd33ce87
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571429"
---
# <a name="iactivescriptparseprocedureold-interface"></a>Интерфейс IActiveScriptParseProcedureOld
Позволяет добавлять текст исходного кода для процедур, добавляемых в скрипт. Для интерпретируемых языков сценариев, которые не имеют независимой среды разработки, такой как VBScript, это предоставляет альтернативный механизм (отличный от `IActiveScriptParse` или `IPersist*`) для добавления процедур сценариев в пространство имен.  
  
> [!NOTE]
> Этот интерфейс не рекомендуется использовать в качестве предпочтительного интерфейса `IActiveScriptParseProcedure`.  
  
## <a name="methods"></a>Методы  
 В дополнение к методам, унаследованным от `IUnknown`, интерфейс `IActiveScriptParseProcedureOld` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Анализирует данную процедуру кода и добавляет процедуру в пространство имен.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)
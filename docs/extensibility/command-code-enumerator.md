---
title: Перечислитель кода команды | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddb2e88db15d60731bc17fcc60cb69772779f14e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927014"
---
# <a name="command-code-enumerator"></a>Перечислитель кода команды
Этот перечислитель используется в параметрах [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и [SccPopulateList](../extensibility/sccpopulatelist-function.md)для указания команды, для которого задаются параметры.

## <a name="syntax"></a>Синтаксис

```
enum SCCCOMMAND {
   SCC_COMMAND_GET,
   SCC_COMMAND_CHECKOUT,
   SCC_COMMAND_CHECKIN,
   SCC_COMMAND_UNCHECKOUT,
   SCC_COMMAND_ADD,
   SCC_COMMAND_REMOVE,
   SCC_COMMAND_DIFF,
   SCC_COMMAND_HISTORY,
   SCC_COMMAND_RENAME,
   SCC_COMMAND_PROPERTIES,
   SCC_COMMAND_OPTIONS
};
```

## <a name="members"></a>Участники
Соответствует SCC_COMMAND_GET [SccGet](../extensibility/sccget-function.md).

Соответствует SCC_COMMAND_CHECKOUT [SccCheckout](../extensibility/scccheckout-function.md).

Соответствует SCC_COMMAND_CHECKIN [SccCheckin](../extensibility/scccheckin-function.md).

Соответствует SCC_COMMAND_UNCHECKOUT [SccUncheckout](../extensibility/sccuncheckout-function.md).

Соответствует SCC_COMMAND_ADD [SccAdd](../extensibility/sccadd-function.md).

Соответствует SCC_COMMAND_REMOVE [SccRemove](../extensibility/sccremove-function.md).

Соответствует SCC_COMMAND_DIFF [SccDiff](../extensibility/sccdiff-function.md).

Соответствует SCC_COMMAND_HISTORY [SccHistory](../extensibility/scchistory-function.md).

Соответствует SCC_COMMAND_RENAME [SccRename](../extensibility/sccrename-function.md).

Соответствует SCC_COMMAND_PROPERTIES [SccProperties](../extensibility/sccproperties-function.md).

Соответствует SCC_COMMAND_OPTIONS [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>См. также
- [Подключаемых модулей системы управления версиями](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)

---
title: Командный код Enumerator Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15916d26ac0120417205af0bb9117a45ec0397c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739797"
---
# <a name="command-code-enumerator"></a>Перечисление командного кода
Этот регистратор используется в опциях [Для SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и [SccPopulateList](../extensibility/sccpopulatelist-function.md)для обозначения команды, для которой указаны параметры.

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
SCC_COMMAND_GET соответствует [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT соответствует [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN соответствует [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT соответствует [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD соответствует [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE соответствует [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF соответствует [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY соответствует [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME соответствует [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES соответствует [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS соответствует [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>См. также
- [Плагины управления исходным элементом](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)

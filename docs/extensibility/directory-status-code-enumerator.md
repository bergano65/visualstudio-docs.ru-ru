---
title: Перечислитель кода состояния каталога | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b6e113949c9e87605895bbb43aa1ae4b4df0496
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348038"
---
# <a name="directory-status-code-enumerator"></a>Перечислитель кода состояния каталога
`SccDirStatus` Перечислитель содержит именованные константы, определяющие состояние каталога в системе управления версиями. Это перечисление используется с [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Это была введена в версии 1.2 API подключаемых модулей управления источника.

## <a name="syntax"></a>Синтаксис

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Участники
 Не удалось получить состояние SCC_DIRSTATUS_INVALID; не следует полагаться на него.

 SCC_DIRSTATUS_NOTCONTROLLED каталог не существует в системе управления версиями.

 Каталог SCC_DIRSTATUS_CONTROLLED находится в системе управления версиями.

 SCC_DIRSTATUS_EMPTYPROJ проекта, соответствующий в этот каталог является пустым.

## <a name="see-also"></a>См. также
- [Подключаемых модулей системы управления версиями](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
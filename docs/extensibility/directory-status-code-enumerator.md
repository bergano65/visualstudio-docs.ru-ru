---
title: Перечислитель кода состояния каталога | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b5ebf61f2baa6e4277e27cd3c4d18a51e64f835
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712156"
---
# <a name="directory-status-code-enumerator"></a>Перечислитель кода состояния каталога
`SccDirStatus`Перечислитель содержит именованные постоянные значения, указывающие состояние каталога в системе управления версиями. Это перечисление используется [сккдиркуеринфо](../extensibility/sccdirqueryinfo-function.md). Это было представлено в версии 1,2 API подключаемого модуля системы управления версиями.

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
 Не удалось получить состояние SCC_DIRSTATUS_INVALID; не полагайтесь на нее.

 SCC_DIRSTATUS_NOTCONTROLLED каталог не находится в системе управления версиями.

 SCC_DIRSTATUS_CONTROLLED Directory находится в системе управления версиями.

 Проект SCC_DIRSTATUS_EMPTYPROJ, соответствующий этому каталогу, пуст.

## <a name="see-also"></a>См. также
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)

---
title: Перечислитель кода состояния файла | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50312caddf0ce2b5c64d1ec83e1707e2e0ee086e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863068"
---
# <a name="file-status-code-enumerator"></a>Перечислитель кода состояния файла
`SccStatus` Перечислитель содержит именованные константы, определяющие состояние файла в системе управления версиями. Это перечисление используется с [SccQueryInfo](../extensibility/sccqueryinfo-function.md) и `POPLISTFUNC` функцию обратного вызова (см. в разделе [POPLISTFUNC](../extensibility/poplistfunc.md) сведения).

## <a name="syntax"></a>Синтаксис

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Участники
 Не удалось получить состояние SCC_STATUS_INVALID; не следует полагаться на него.

 Файл SCC_STATUS_NOTCONTROLLED не в системе управления версиями.

 Файл SCC_STATUS_CONTROLLED находится в системе управления версиями.

 SCC_STATUS_CHECKEDOUT флажок установлен, текущий пользователь на локальном диске.

 SCC_STATUS_OUTOTHER файл извлечен другим пользователем.

 Исключительно SCC_STATUS_OUTEXCLUSIVE файл извлечен.

 SCC_STATUS_OUTMULTIPLE файл извлечен более чем одним пользователем.

 SCC_STATUS_OUTOFDATE файл не является последней.

 SCC_STATUS_DELETED файл был удален из проекта.

 SCC_STATUS_LOCKED файл заблокирован; Допускается наличие нескольких версий.

 Файл SCC_STATUS_MERGED были объединены, но еще не исправлены и проверены.

 Файл SCC_STATUS_SHARED распределяется между проектами.

 Файл SCC_STATUS_PINNED будет доступно для версии явно.

 SCC_STATUS_MODIFIED файл был изменен или разбить/нарушено.

 SCC_STATUS_OUTBYUSER файл извлечен текущим пользователем.

 Файл SCC_STATUS_NOMERGE никогда не могут быть объединены с и нет необходимости сохранять до запроса GET.

 SCC_STATUS_RESERVED_1 зарезервированы для внутреннего использования.

 SCC_STATUS_RESERVED_2 зарезервированы для внутреннего использования.

## <a name="see-also"></a>См. также
- [Подключаемых модулей системы управления версиями](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
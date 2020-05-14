---
title: Код кода файла Enumerator (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 184c8686ea184aea2cbd0a64873718cbe72f7615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711451"
---
# <a name="file-status-code-enumerator"></a>Перечисление кода файла
Регистратор `SccStatus` содержит именованные постоянные значения, которые определяют состояние файла в системе управления исходным источником. Этот перечисление используется [Scc'eryInfo](../extensibility/sccqueryinfo-function.md) и `POPLISTFUNC` функцией обратного вызова (подробнее см. [POPLISTFUNC).](../extensibility/poplistfunc.md)

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
 SCC_STATUS_INVALID статус не может быть получен; не полагайтесь на него.

 SCC_STATUS_NOTCONTROLLED файл не находится под контролем источника.

 SCC_STATUS_CONTROLLED файл находится под контролем источника.

 SCC_STATUS_CHECKEDOUT Проверено текущим пользователем на локальном диске.

 SCC_STATUS_OUTOTHER файл проверяется другим пользователем.

 SCC_STATUS_OUTEXCLUSIVE файл исключительно проверяется.

 SCC_STATUS_OUTMULTIPLE файл проверяется более чем одним пользователем.

 SCC_STATUS_OUTOFDATE Файл не самый недавний.

 SCC_STATUS_DELETED файл был удален из проекта.

 SCC_STATUS_LOCKED файл заблокирован; больше не допускается версий.

 SCC_STATUS_MERGED файл был объединен, но еще не исправлена/проверена.

 SCC_STATUS_SHARED файл амеразийный между проектами.

 SCC_STATUS_PINNED файл амебь явная версия.

 SCC_STATUS_MODIFIED файл был изменен/сломан/нарушен.

 SCC_STATUS_OUTBYUSER файл проверяется текущим пользователем.

 SCC_STATUS_NOMERGE файл никогда не может быть объединен с и не должны быть сохранены до GET.

 SCC_STATUS_RESERVED_1 зарезервированы для внутреннего использования.

 SCC_STATUS_RESERVED_2 зарезервированы для внутреннего использования.

## <a name="see-also"></a>См. также
- [Плагины управления исходным элементом](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)

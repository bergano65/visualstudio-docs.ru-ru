---
title: Регистратор кода каталога (ru) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712156"
---
# <a name="directory-status-code-enumerator"></a>Перечисление кода каталога
Регистратор `SccDirStatus` содержит именованные постоянные значения, определяющие состояние каталога в системе управления исходным источником. Этот перечисление используется [SccDir-EryInfo](../extensibility/sccdirqueryinfo-function.md). Это было введено в версии 1.2 API подключаемого элемента управления исходным управлением.

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
 SCC_DIRSTATUS_INVALID статус не может быть получен; не полагайтесь на него.

 SCC_DIRSTATUS_NOTCONTROLLED каталог не находится под контролем источника.

 SCC_DIRSTATUS_CONTROLLED каталог находится под контролем источника.

 SCC_DIRSTATUS_EMPTYPROJ проект, соответствующий этому каталогу, пуст.

## <a name="see-also"></a>См. также
- [Плагины управления исходным элементом](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)

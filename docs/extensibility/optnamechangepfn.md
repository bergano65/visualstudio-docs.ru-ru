---
title: OPTNAMECHANGEPFN Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 603bd08c1ec3832bf732e0b33101076738d009e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702251"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Это функция обратного вызова, указанная в вызове в `SCC_OPT_NAMECHANGEPFN` [SccSetOption](../extensibility/sccsetoption-function.md) (с использованием опции) и используется для передачи изменений имен, внесенных плагином управления исходным управлением обратно в IDE.

## <a name="signature"></a>Сигнатура

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Параметры
 pvCallerData

(в) Значение пользователя, указанное в предыдущем вызове на `SCC_OPT_USERDATA` [SccSetOption](../extensibility/sccsetoption-function.md) (с использованием опции).

 pszOldName

(в) Исходное имя файла.

 pszNewName

(в) Имя файла было переименовано.

## <a name="return-value"></a>Возвращаемое значение
 Нет.

## <a name="remarks"></a>Примечания
 Если файл переименован во время операции управления исходным источником, плагин управления исходным элементом может уведомить IDE об изменении имени с помощью этого обратного вызова.

 Если IDE не поддерживает этот обратный вызов, он не будет называть [SccSetOption,](../extensibility/sccsetoption-function.md) чтобы указать его. Если плагин не поддерживает этот обратный вызов, он вернется `SCC_E_OPNOTSUPPORTED` из `SccSetOption` функции, когда IDE попытается установить обратный вызов.

## <a name="see-also"></a>См. также
- [Функции обратного вызова, реализованные IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)

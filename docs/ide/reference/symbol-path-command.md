---
title: Команда Symbol Path
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22a27d795e5491081dca98a395c788cf8407e43e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942774"
---
# <a name="symbol-path-command"></a>Команда Symbol Path
Задает список каталогов для поиска символов отладчиком.

## <a name="syntax"></a>Синтаксис

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Аргументы
 `pathname`

 Необязательный. Список путей, разделенных точкой с запятой, для поиска символов отладчиком.

## <a name="remarks"></a>Примечания
 Если `pathname` не указан, эта команда выводит список текущих путей к символам.

## <a name="example"></a>Пример
 Этот пример добавляет два пути в список каталогов символов.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Пример
 Этот пример отображает список текущих путей к символам, разделенных точкой с запятой.

```
Debug.SymbolPath
```

## <a name="see-also"></a>См. также

- [Командное окно](../../ide/reference/command-window.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
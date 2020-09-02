---
title: Команда "Путь к символам" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d02d4cfede6ed3499d09ff58e4454c1ef9cbe0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651006"
---
# <a name="symbol-path-command"></a>Команда Symbol Path
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает список каталогов для поиска символов отладчиком.

## <a name="syntax"></a>Синтаксис

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Аргументы
 `pathname` Необязательный. Список путей, разделенных точкой с запятой, для поиска символов отладчиком.

## <a name="remarks"></a>Remarks
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

## <a name="see-also"></a>См. также:
 [Command Window](../../ide/reference/command-window.md) [Команды Visual Studio](../../ide/reference/visual-studio-commands.md) командное окно

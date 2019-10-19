---
title: Команда "Открыть проект" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99596442f3aef9e4cb2d890438d29b96cdf4f083
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671924"
---
# <a name="open-project-command"></a>Команда Open Project
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Открывает существующий проект.

## <a name="syntax"></a>Синтаксис

```
File.OpenProject filename
```

## <a name="arguments"></a>Аргументы
 `filename` Обязательный. Полный путь и имя файла для открываемого проекта.

 В соответствии с требованиями синтаксиса для аргумента `filename` путь, содержащий пробелы, должен заключаться в кавычки.

## <a name="remarks"></a>Примечания
 Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода.

 Эта команда недоступна при отладке.

## <a name="example"></a>Пример
 Этот пример открывает проект [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] — Test1.

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>См. также
 Команды [Visual Studio командное](../../ide/reference/visual-studio-commands.md) [окно](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) командные [псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)

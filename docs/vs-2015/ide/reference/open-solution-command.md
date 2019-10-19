---
title: Команда "Открыть решение" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9c9ab66d2885137e9c470f577996ab861b554d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671909"
---
# <a name="open-solution-command"></a>Команда Open Solution
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Открывает существующее решение, закрывая все другие открытые решения.

## <a name="syntax"></a>Синтаксис

```
File.OpenSolution filename
```

## <a name="arguments"></a>Аргументы
 `Filename` Обязательный. Полный путь и имя файла открываемого решения.

 В соответствии с требованиями синтаксиса для аргумента `filename` путь, содержащий пробелы, должен заключаться в кавычки.

## <a name="remarks"></a>Примечания
 Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода.

## <a name="example"></a>Пример
 В этом примере открывается решение Test1.sln.

```
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"
```

## <a name="see-also"></a>См. также
 Команды [Visual Studio командное](../../ide/reference/visual-studio-commands.md) [окно](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) командные [псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)

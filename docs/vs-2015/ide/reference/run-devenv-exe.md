---
title: -Run (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b2716995e8ff3a318262284b5733a471086c68c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665526"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Компилирует и запускает указанный проект или указанное решение.

## <a name="syntax"></a>Синтаксис

```
devenv {/run|/r} {SolutionName|ProjectName}
```

## <a name="arguments"></a>Аргументы
 `SolutionName` Обязательный. Полный путь и имя для файла решения.

 `ProjectName` Обязательный. Полный путь и имя для файла проекта.

## <a name="remarks"></a>Remarks
 Компилирует и запускает указанный проект или указанное решение согласно параметрам, заданным для активной конфигурации решения. Этот параметр запускает интегрированную среду разработки (IDE), которая остается активной после завершения выполнения проекта или решения.

- Строки с пробелами заключаются в двойные кавычки.

- Сводные данные, включая ошибки, могут отображаться в окне **Команда** или в любом файле журнала, указанном с помощью параметра `/out`.

## <a name="example"></a>Пример
 Этот пример запускает решение `MySolution`, используя активную конфигурацию развертывания.

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>См. также:
 [Параметры командной строки devenv](../../ide/reference/devenv-command-line-switches.md) [/runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/REBUILD (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)

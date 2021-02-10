---
title: -Run (devenv.exe)
description: Узнайте, как использовать параметр командной строки Run devenv для компиляции и запуска указанного проекта или решения.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Run Devenv
- Run Devenv switch
- applications [Visual Studio], running
- /R Devenv switch
- Devenv, /Run switch
- R Devenv switch (/R)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 34e9f50f864f8f2908a3822befda0652df6a3340
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957924"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)

Компилирует и запускает указанный проект или указанное решение.

## <a name="syntax"></a>Синтаксис

```shell
devenv {/Run|/R} {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Аргументы

- *SolutionName*

  Полный путь и имя для файла решения.

- *Имя проекта*

  Полный путь и имя для файла проекта.

- `/Out` *OutputFilename*

  Необязательный элемент. Имя файла, в который вы хотите отправить выходные данные средства. Если файл уже существует, средство добавляет в его конец выходные данные.

## <a name="remarks"></a>Комментарии

Компилирует и запускает указанный проект или указанное решение согласно параметрам, заданным для активной конфигурации решения. Этот параметр запускает интегрированную среду разработки, которая остается активной после завершения выполнения проекта или решения.

- Строки с пробелами заключаются в двойные кавычки.

- Сводные данные, включая ошибки, могут отображаться в окне **Команда** или в любом файле журнала, указанном с помощью параметра `/Out`.

## <a name="example"></a>Пример

Этот пример запускает решение `MySolution`, используя активную конфигурацию развертывания.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)

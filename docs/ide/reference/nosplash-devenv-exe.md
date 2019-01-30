---
title: -NoSplash (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f11b44833ae54c6982cc4df9e2dbd6cb03e7fcd1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927897"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Отключает отображение экрана-заставки.

## <a name="syntax"></a>Синтаксис

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Аргументы

- *File1*

  Необязательный параметр. Файл, открываемый в существующем экземпляре Visual Studio. Если экземпляр Visual Studio отсутствует, в упрощенном окне создается новый экземпляр, в котором открывается *File1*.

- *FileN*

  Необязательный параметр. Один или несколько дополнительных файлов для открытия в существующем экземпляре Visual Studio.

## <a name="remarks"></a>Примечания

Этот параметр скрывает экран-заставку. Если этот параметр не задан, экран-заставка отображается. Для отображения экрана-заставки в дальнейшем (например, для проверки логотипа продукта VSPackage) необходимо использовать параметр [/Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

Параметр `/NoSplash` можно использовать вместе с другими параметрами, например [/Run](run-devenv-exe.md) или [/DebugExe](debugexe-devenv-exe.md).

## <a name="example"></a>Пример

Все три примера запускают интегрированную среду разработки без отображения экрана-заставки. Второй пример также компилирует указанное решение и запускает созданный исполняемый файл. Третий пример открывает указанный исполняемый файл открывается для отладки в интегрированной среде разработки.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [Параметры командной строки devenv для разработки VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)

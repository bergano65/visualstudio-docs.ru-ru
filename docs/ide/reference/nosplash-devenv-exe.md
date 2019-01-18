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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 794934ab0bddcc90a36accf639b26e5ecc6bab30
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2019
ms.locfileid: "54233152"
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

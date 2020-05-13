---
title: СоздатьPkgDef Утилита (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709169"
---
# <a name="createpkgdef-utility"></a>Создание утилиты PkgDef
Принимает файл .dll для расширения Visual Studio в качестве параметра и создает файл *.pkgdef* для сопровождения файла *.dll.* Файл *.pkgdef* содержит всю информацию, которая в противном случае была бы записана в системный реестр при установке расширения.

> [!NOTE]
> Большинство шаблонов проекта, включенных в Visual Studio SDK, автоматически создают файлы *.pkgdef* в процессе сборки. Этот документ предназначен для тех, кто хочет создавать пакеты вручную или преобразовывать существующие пакеты в развертывание *.pkgdef.*

## <a name="syntax"></a>Синтаксис

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Аргументы
**/вне"&lt;FileName&gt;**\
Обязательный элемент. Устанавливает имя выходного файла *.pkgdef* в &lt;FileName.&gt;

**/Код-база**\
Необязательный параметр. Регистрация сил в службе **CodeBase.**

**/сборка**\
Регистрация сил в **службе собрания.**

**&lt;СборкаПат&gt;**\
Путь файла *.dll,* из которого вы хотите создать *.pkgdef.*

## <a name="remarks"></a>Примечания
Развертывание расширения с помощью файлов *.pkgdef* заменяет требования реестра более ранних версий Visual Studio.

::: moniker range=">=vs-2019"

Файлы *.pkgdef* должны быть установлены в одном из следующих мест:

- *%localappdata% »Microsoft-Visual Studio»16.0\\*

- *%vsinstalldir%-Common7-IDE-Расширения\\*

Если папка установки *составляет %localappdata% -"Microsoft-Visual Studio"16.0\\"Расширения",* расширение распознается Visual Studio, но отключенпо умолчанию. Пользователь может включить расширение с помощью **расширения управления.**

Если папка установки *составляет %vsinstalldir%-Common7-IDE-Расширения,\\*расширение включено по умолчанию.

> [!NOTE]
> Инструмент **управления расширениями** не может использоваться для доступа к расширению, если он не установлен как часть пакета VSIX.

::: moniker-end

::: moniker range="vs-2017"

Файлы *.pkgdef* должны быть установлены в одном из следующих мест:

- *%localappdata% »Microsoft-Visual Studio»15.0\\*

- *%vsinstalldir%-Common7-IDE-Расширения\\*

Если папка установки *составляет %localappdata% -"Microsoft-Visual Studio"15.0\\"Расширения",* расширение распознается Visual Studio, но отключенпо умолчанию. Пользователь может включить расширение с помощью **расширений и обновлений.**

Если папка установки *составляет %vsinstalldir%-Common7-IDE-Расширения,\\*расширение включено по умолчанию.

> [!NOTE]
> Инструмент **расширения и обновления** не может использоваться для доступа к расширению, если он не установлен как часть пакета VSIX.

::: moniker-end

## <a name="see-also"></a>См. также
- [Утилита CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)

---
title: Служебная программа CreatePkgDef | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ab5866949d6ccfa9f3b1037abf7801ce40ace3d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332285"
---
# <a name="createpkgdef-utility"></a>Служебная программа CreatePkgDef
Принимает DLL-файла для расширения Visual Studio, как параметр и создает *.pkgdef* файл сопровождающее *.dll* файл. *.Pkgdef* файл содержит всю информацию, которая в противном случае должна быть записана в системный реестр при установке расширения.

> [!NOTE]
> Большая часть шаблонов проектов, которые включены в пакет SDK для Visual Studio автоматически создать *.pkgdef* файлы как часть процесса построения. Данный документ предназначен для тех, которые хотят создать пакеты вручную или преобразовать существующие пакеты для использования *.pkgdef* развертывания.

## <a name="syntax"></a>Синтаксис

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Аргументы
**/ out =&lt;имя файла&gt;** \
Обязательный. Задает имя *.pkgdef* выходной файл &lt;FileName&gt;.

**/ codebase**\
Необязательный параметр. Заставляет регистрации с **CodeBase** служебной программы.

**/ Assembly**\
Заставляет регистрации с **сборки** служебной программы.

**&lt;AssemblyPath&gt;** \
Путь к *.dll* файла, из которого требуется создать *.pkgdef*.

## <a name="remarks"></a>Примечания
Развертывание расширения с помощью *.pkgdef* файлов заменяет требования реестра из более ранних версиях Visual Studio.

::: moniker range=">=vs-2019"

*.Pkgdef* файлы должны быть установлены в одном из следующих расположений:

- *%LocalAppData%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Если папка установки *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\* , расширение распознается средой Visual Studio, но отключена по умолчанию. Пользователь может включить расширение с помощью **Управление расширениями**.

Если папка установки *%vsinstalldir%\Common7\IDE\Extensions\\* , расширение включено по умолчанию.

> [!NOTE]
> **Управление расширениями** средство не может использоваться для доступа к расширением, если он не установлен как часть пакета VSIX.

::: moniker-end

::: moniker range="vs-2017"

*.Pkgdef* файлы должны быть установлены в одном из следующих расположений:

- *%LocalAppData%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Если папка установки *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\* , расширение распознается средой Visual Studio, но отключена по умолчанию. Пользователь может включить расширение с помощью **расширения и обновления**.

Если папка установки *%vsinstalldir%\Common7\IDE\Extensions\\* , расширение включено по умолчанию.

> [!NOTE]
> **Расширения и обновления** средство не может использоваться для доступа к расширением, если он не установлен как часть пакета VSIX.

::: moniker-end

## <a name="see-also"></a>См. также
- [Служебная программа CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)

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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709169"
---
# <a name="createpkgdef-utility"></a>Служебная программа CreatePkgDef
Принимает DLL-файл для расширения Visual Studio в качестве параметра и создает *pkgdef* -файл, сопровождающий *DLL* -файл. Файл *pkgdef* содержит все данные, которые в противном случае были бы записаны в системный реестр при установке расширения.

> [!NOTE]
> Большинство шаблонов проектов, включенных в пакет SDK для Visual Studio, автоматически создают файлы *pkgdef* в рамках процесса сборки. Этот документ предназначен для тех, кто хочет создавать пакеты вручную, или преобразовать существующие пакеты для развертывания *. pkgdef*  .

## <a name="syntax"></a>Синтаксис

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Аргументы
**/out = &lt; имя файла&gt;**\
Обязательный. Задает имя файла выходных данных *. pkgdef* &lt; &gt; .

**/CodeBase**\
Необязательный элемент. Принудительная регистрация с помощью служебной программы **CodeBase** .

**/Assembly**\
Принудительная регистрация с помощью служебной программы **сборки** .

**&lt;AssemblyPath&gt;**\
Путь к *DLL* -файлу, из которого нужно создать *pkgdef*-файл.

## <a name="remarks"></a>Remarks
Развертывание расширения с помощью файлов *pkgdef* заменяет требования к реестру в более ранних версиях Visual Studio.

::: moniker range=">=vs-2019"

Файлы *pkgdef* должны быть установлены в одном из следующих расположений:

- *%Локалаппдата%\микрософт\висуал Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Если папка установки — *%Локалаппдата%\микрософт\висуал Studio\16.0\Extensions \\ *, расширение распознается Visual Studio, но по умолчанию отключено. Пользователь может включить расширение, используя **Управление расширениями**.

Если папка установки — *%vsinstalldir%\Common7\IDE\Extensions \\ *, расширение включено по умолчанию.

> [!NOTE]
> Средство **Управление расширениями** не может использоваться для доступа к расширению, если оно не установлено как часть пакета VSIX.

::: moniker-end

::: moniker range="vs-2017"

Файлы *pkgdef* должны быть установлены в одном из следующих расположений:

- *%Локалаппдата%\микрософт\висуал Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Если папка установки — *%Локалаппдата%\микрософт\висуал Studio\15.0\Extensions \\ *, расширение распознается Visual Studio, но по умолчанию отключено. Пользователь может включить расширение с помощью **расширений и обновлений**.

Если папка установки — *%vsinstalldir%\Common7\IDE\Extensions \\ *, расширение включено по умолчанию.

> [!NOTE]
> Средство " **расширения и обновления** " нельзя использовать для доступа к расширению, если оно не установлено как часть пакета VSIX.

::: moniker-end

## <a name="see-also"></a>См. также раздел
- [Служебная программа CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)

---
title: -Edit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26433d62a68b28450a56eee1282376733acfe55c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911914"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Открывает указанный файл в существующем экземпляре Visual Studio.

## <a name="syntax"></a>Синтаксис

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Аргументы

- *File1*

  Необязательный параметр. Файл, открываемый в существующем экземпляре Visual Studio. Если экземпляр Visual Studio отсутствует, в упрощенном окне создается новый экземпляр, в котором открывается *File1*.

- *FileN*

  Необязательный параметр. Один или несколько дополнительных файлов для открытия в существующем экземпляре Visual Studio.

## <a name="remarks"></a>Примечания

Если файл не указан, используется существующий экземпляр Visual Studio. Если файл не указан и экземпляр Visual Studio отсутствует, создается новый экземпляр с упрощенным макетом окна.

Если существующий экземпляр Visual Studio находится в модальном состоянии, файл открывается в существующем экземпляре, когда Visual Studio выходит из модального состояния. Например, такая ситуация может возникнуть, когда открыто диалоговое окно [Параметры](../../ide/reference/options-dialog-box-visual-studio.md).

## <a name="example"></a>Пример

Первый пример открывает файл `MyFile.cs` в существующем экземпляре Visual Studio. Если экземпляр Visual Studio отсутствует, средство открывает файл в новом экземпляре. Второй пример аналогичным образом открывает три файла вместо одного.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
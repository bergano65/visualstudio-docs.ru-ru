---
title: Команда List Source
description: Узнайте о команде List Source и о том, как она позволяет отобразить указанные строки исходного кода.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae2463a3d8dd295fcba9bf264e1ad3fa250169d4
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305287"
---
# <a name="list-source-command"></a>Команда List Source
Отображает заданные строки исходного кода.

## <a name="syntax"></a>Синтаксис

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Коммутаторы
/Count:`number`

Необязательный параметр. Указание числа строк для отображения.

/Current

Необязательный параметр. Отображение текущей строки.

/File:`filename`

Необязательный параметр. Путь к файлу для отображения. Если имя файла не указано, при выполнении команды выводится исходный код строки текущего оператора.

/Line:`number`

Необязательный параметр. Отображение определенного номера строки.

/ShowLineNumbers:`yes|no`

Необязательный параметр. Указание отображения номеров строк.

## <a name="example"></a>Пример
В приведенном ниже примере показан исходный код со строки 4 файла Form1.vb с отображением номеров строк.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
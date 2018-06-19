---
title: Команда List Source
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03a5d0699fced4d01d439942081b359454bcf476
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943622"
---
# <a name="list-source-command"></a>Команда List Source
Отображает заданные строки исходного кода.

## <a name="syntax"></a>Синтаксис

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Переключатели
 /Count:`number`

 Необязательный. Указание числа строк для отображения.

 /Current

 Необязательный. Отображение текущей строки.

 /File:`filename`

 Необязательный. Путь к файлу для отображения. Если имя файла не указано, при выполнении команды выводится исходный код строки текущего оператора.

 /Line:`number`

 Необязательный. Отображение определенного номера строки.

 /ShowLineNumbers:`yes|no`

 Необязательный. Указание отображения номеров строк.

## <a name="example"></a>Пример
 В приведенном ниже примере показан исходный код со строки 4 файла Form1.vb с отображением номеров строк.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
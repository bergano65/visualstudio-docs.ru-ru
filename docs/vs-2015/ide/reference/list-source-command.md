---
title: Команда "Вывести исходный код" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f13689b6e3ac4db2d58c1def3a5d0dd05c219f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672323"
---
# <a name="list-source-command"></a>Команда List Source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображает заданные строки исходного кода.

## <a name="syntax"></a>Синтаксис

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Переключатели
 /Count: `number` необязательный. Указание числа строк для отображения.

 /Куррент необязательный. Отображение текущей строки.

 /File: `filename` необязательный. Путь к файлу для отображения. Если имя файла не указано, при выполнении команды выводится исходный код строки текущего оператора.

 /Лине: `number` необязательный. Отображение определенного номера строки.

 /Шовлиненумберс: `yes|no` необязательный. Указание отображения номеров строк.

## <a name="remarks"></a>Примечания

## <a name="example"></a>Пример
 В приведенном ниже примере показан исходный код со строки 4 файла Form1.vb с отображением номеров строк.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>См. также
 [Окно](../../ide/reference/command-window.md) команд в командах [Visual Studio](../../ide/reference/visual-studio-commands.md)

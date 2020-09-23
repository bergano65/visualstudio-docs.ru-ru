---
title: Поиск библиотеки DLL, в которой произошел сбой программы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4432378e10590c2ba930edf0920b9146e450f96
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852078"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Практическое руководство. Поиск библиотеки DLL, в которой произошел сбой программы (C#, C++, Visual Basic, F#)

 Если приложение аварийно завершает работу при вызове системных DLL или какого-то другого кода, необходимо найти, какие библиотеки DLL были активны в момент возникновения сбоя. Если сбой библиотеки DLL произошел вне данной программы, то его источник можно определить с помощью окна **Модули**.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Чтобы определить место сбоя при помощи окна Модули

1. Запишите адрес, по которому происходит сбой.

    Если адрес не отображается в сообщении об ошибке, используйте альтернативные методы поиска библиотеки DLL. Если есть подозрительная системная библиотека DLL, можно [загрузить символы](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) с серверов символов Майкрософт при отладке. В противном случае вы можете [создать файл дампа](../debugger/using-dump-files.md) со сведениями о куче. Для создания файлов дампа доступны разные [средства](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/).

2. В меню **Отладка** выберите пункт **Окна**, а затем **Модули**.

3. В окне **Модули** найдите столбец **Адрес**. В случае необходимости воспользуйтесь полосой прокрутки.

4. Нажмите кнопку **Адрес** (вверху столбца), чтобы отсортировать библиотеки DLL по адресам.

5. Просмотрите отсортированный список и найдите библиотеку DLL, чей диапазон адресов содержит адрес точки сбоя.

6. Посмотрите значения в столбцах **Имя** и **Путь**, чтобы узнать имя и путь библиотеки DLL.

## <a name="see-also"></a>См. также
- [Отладка проектов DLL](../debugger/debugging-dll-projects.md)
- [Практическое руководство. Использование окна модулей](../debugger/how-to-use-the-modules-window.md)
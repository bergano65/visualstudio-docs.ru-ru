---
title: Практическое руководство. Поиск библиотеки DLL которой произошел сбой в программы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b7a9421af9e0caf085feb1afb27b53befe837668
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894051"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Практическое руководство. Поиск библиотеки DLL которой произошел сбой в программы (C#, C++, Visual Basic, F#)

 Если приложение аварийно завершает работу при вызове системных DLL или какого-то другого кода, необходимо найти, какие библиотеки DLL были активны в момент возникновения сбоя. Если сбой библиотеки DLL произошел вне данной программы, то его источник можно определить с помощью окна **Модули**.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Чтобы определить место сбоя при помощи окна Модули

1. Запишите адрес, по которому происходит сбой.

    Если адрес не указывается в сообщении об ошибке, может потребоваться использовать альтернативные методы для идентификации библиотеки DLL. Если вы подозреваете системной библиотеки DLL, вы можете [загрузить символы](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) с серверов символов Майкрософт при отладке. В противном случае может потребоваться [Создание файла дампа](../debugger/using-dump-files.md) с кучи сведения вместо этого. Различные [средства](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) доступны для создания файлов дампа.

2. В меню **Отладка** выберите пункт **Окна**, а затем **Модули**.

3. В окне **Модули** найдите столбец **Адрес**. В случае необходимости воспользуйтесь полосой прокрутки.

4. Нажмите кнопку **Адрес** (вверху столбца), чтобы отсортировать библиотеки DLL по адресам.

5. Просмотрите отсортированный список и найдите библиотеку DLL, чей диапазон адресов содержит адрес точки сбоя.

6. Посмотрите значения в столбцах **Имя** и **Путь**, чтобы узнать имя и путь библиотеки DLL.

## <a name="see-also"></a>См. также
- [Отладка проектов DLL](../debugger/debugging-dll-projects.md)
- [Практическое руководство. Использование окна модулей](../debugger/how-to-use-the-modules-window.md)
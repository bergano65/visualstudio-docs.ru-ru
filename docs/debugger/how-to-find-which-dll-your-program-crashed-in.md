---
title: Как найти библиотеку DLL, в которой произошел сбой программы | Документация Майкрософт
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
ms.openlocfilehash: bff4f164e16a65efe4ec3d1f057025168eab8cd2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733273"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Как найти библиотеку DLL, в которой произошел сбой программы (C#, C++, Visual Basic, F#)

 Если приложение аварийно завершает работу при вызове системных DLL или какого-то другого кода, необходимо найти, какие библиотеки DLL были активны в момент возникновения сбоя. Если сбой библиотеки DLL произошел вне данной программы, то его источник можно определить с помощью окна **Модули**.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Чтобы определить место сбоя при помощи окна Модули

1. Запишите адрес, по которому происходит сбой.

    Если адрес не отображается в сообщении об ошибке, может потребоваться использовать альтернативные методы для поиска библиотеки DLL. Если есть подозрительная системная библиотека DLL, можно [загрузить символы](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) с серверов символов Майкрософт при отладке. В противном случае вместо этого может потребоваться [создать файл дампа](../debugger/using-dump-files.md) с информацией о куче. Для создания файлов дампа доступны различные [средства](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) .

2. В меню **Отладка** выберите пункт **Окна**, а затем **Модули**.

3. В окне **Модули** найдите столбец **Адрес**. В случае необходимости воспользуйтесь полосой прокрутки.

4. Нажмите кнопку **Адрес** (вверху столбца), чтобы отсортировать библиотеки DLL по адресам.

5. Просмотрите отсортированный список и найдите библиотеку DLL, чей диапазон адресов содержит адрес точки сбоя.

6. Посмотрите значения в столбцах **Имя** и **Путь**, чтобы узнать имя и путь библиотеки DLL.

## <a name="see-also"></a>См. также
- [Отладка проектов DLL](../debugger/debugging-dll-projects.md)
- [Практическое руководство. Использование окна модулей](../debugger/how-to-use-the-modules-window.md)
---
title: 'Практическое: поиск библиотеки DLL которой произошел сбой в программы | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40f27e0bec20e1dd037beaa5f60ea648c0ccb171
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257101"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Практическое: поиск библиотеки DLL которой произошел сбой в программы (C#, C++, Visual Basic, F#)
  
 Если приложение аварийно завершает работу при вызове системных DLL или какого-то другого кода, необходимо найти, какие библиотеки DLL были активны в момент возникновения сбоя. Если сбой библиотеки DLL произошел вне данной программы, то можно определить расположение, используя **модули** окна.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Чтобы определить место сбоя при помощи окна Модули  
  
1.  Запишите адрес, по которому происходит сбой.

    Если адрес не указывается в сообщении об ошибке, может потребоваться использовать альтернативные методы для идентификации библиотеки DLL. Если вы подозреваете системной библиотеки DLL, вы можете [загрузить символы](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) с серверов символов Майкрософт при отладке. В противном случае может потребоваться [Создание файла дампа](../debugger/using-dump-files.md) с кучи сведения вместо этого. Различные [средства](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) доступны для создания файлов дампа.
  
2.  На **Отладка** меню, выберите **Windows**и нажмите кнопку **модули**.  
  
3.  В **модули** окна, найдите **адрес** столбца. В случае необходимости воспользуйтесь полосой прокрутки.  
  
4.  Нажмите кнопку **адрес** кнопку в верхней части столбца, чтобы отсортировать библиотеки DLL по адресу.  
  
5.  Просмотрите отсортированный список и найдите библиотеку DLL, чей диапазон адресов содержит адрес точки сбоя.  
  
6.  Рассмотрим **имя** и **путь** столбцы, чтобы узнать имя DLL-файла и путь.  
  
## <a name="see-also"></a>См. также  
 [Отладка проектов DLL](../debugger/debugging-dll-projects.md)   
 [Практическое руководство. Использование окна модулей](../debugger/how-to-use-the-modules-window.md)
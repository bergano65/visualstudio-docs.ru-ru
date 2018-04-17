---
title: 'Как: найти какие DLL руководство | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: 5aca05ea9ab8010ba91592b766de796636f3eb96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Практическое руководство. Поиск библиотеки DLL, в которой произошел сбой программы
  
 Если приложение аварийно завершает работу при вызове системных DLL или какого-то другого кода, необходимо найти, какие библиотеки DLL были активны в момент возникновения сбоя. Если сбой библиотеки DLL произошел вне данной программы, можно определить местоположение с помощью **модули** окна.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Чтобы определить место сбоя при помощи окна Модули  
  
1.  Запишите адрес, по которому происходит сбой.

    Если адрес не отображается в сообщении об ошибке, может потребоваться использовать альтернативные методы для идентификации библиотеки DLL. Если вы подозреваете системных DLL, вы можете [загрузить символы](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) с серверов символов Майкрософт при отладке. В противном случае может потребоваться [Создание файла дампа](../debugger/using-dump-files.md) с кучи сведения вместо него. Различные [средства](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) доступны для создания файлов дампа.
  
2.  На **отладки** меню, выберите **Windows**и нажмите кнопку **модулей**.  
  
3.  В **модули** окна, найдите **адрес** столбца. В случае необходимости воспользуйтесь полосой прокрутки.  
  
4.  Нажмите кнопку **адрес** кнопку в верхней части столбца, чтобы отсортировать библиотеки DLL по адресам.  
  
5.  Просмотрите отсортированный список и найдите библиотеку DLL, чей диапазон адресов содержит адрес точки сбоя.  
  
6.  Посмотрите на **имя** и **путь** столбцы, чтобы узнать имя DLL-файла и путь.  
  
## <a name="see-also"></a>См. также  
 [Отладка проектов DLL](../debugger/debugging-dll-projects.md)   
 [Практическое руководство. Использование окна модулей](../debugger/how-to-use-the-modules-window.md)
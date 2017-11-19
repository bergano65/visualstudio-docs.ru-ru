---
title: "Как: найти какие DLL руководство | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.dll
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
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6232f86e9e9f5d59e9e109d08b75120cc90902c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Практическое руководство. Поиск библиотеки DLL, в которой произошел сбой программы
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, в меню "Сервис" выберите команду "Импорт и экспорт параметров". Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Если приложение аварийно завершает работу при вызове системных DLL или какого-то другого кода, необходимо найти, какие библиотеки DLL были активны в момент возникновения сбоя. Если сбой библиотеки DLL произошел вне данной программы, можно определить местоположение с помощью **модули** окна.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Чтобы определить место сбоя при помощи окна Модули  
  
1.  Запишите адрес, по которому происходит сбой.  
  
2.  На **отладки** меню, выберите **Windows**и нажмите кнопку **модулей**.  
  
3.  В **модули** окна, найдите **адрес** столбца. В случае необходимости воспользуйтесь полосой прокрутки.  
  
4.  Нажмите кнопку **адрес** кнопку в верхней части столбца, чтобы отсортировать библиотеки DLL по адресам.  
  
5.  Просмотрите отсортированный список и найдите библиотеку DLL, чей диапазон адресов содержит адрес точки сбоя.  
  
6.  Посмотрите на **имя** и **путь** столбцы, чтобы узнать имя DLL-файла и путь.  
  
## <a name="see-also"></a>См. также  
 [Отладка проектов DLL](../debugger/debugging-dll-projects.md)   
 [Практическое руководство. Использование окна модулей](../debugger/how-to-use-the-modules-window.md)
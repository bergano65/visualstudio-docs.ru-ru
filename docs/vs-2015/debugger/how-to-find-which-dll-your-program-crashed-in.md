---
title: 'Практическое: поиск библиотеки DLL которой произошел сбой в программы | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 469d4a3f42fc749a0a7a05f4a034bde28332dc57
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183174"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Практическое руководство. Поиск библиотеки DLL, в которой произошел сбой программы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ПРИМЕЧАНИЕ.]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, в меню "Сервис" выберите команду "Импорт и экспорт параметров". Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Если приложение аварийно завершает работу при вызове системных DLL или какого-то другого кода, необходимо найти, какие библиотеки DLL были активны в момент возникновения сбоя. Если сбой библиотеки DLL произошел вне данной программы, то можно определить расположение, используя **модули** окна.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Чтобы определить место сбоя при помощи окна Модули  
  
1.  Запишите адрес, по которому происходит сбой.  
  
2.  На **Отладка** меню, выберите **Windows**и нажмите кнопку **модули**.  
  
3.  В **модули** окна, найдите **адрес** столбца. В случае необходимости воспользуйтесь полосой прокрутки.  
  
4.  Нажмите кнопку **адрес** кнопку в верхней части столбца, чтобы отсортировать библиотеки DLL по адресу.  
  
5.  Просмотрите отсортированный список и найдите библиотеку DLL, чей диапазон адресов содержит адрес точки сбоя.  
  
6.  Рассмотрим **имя** и **путь** столбцы, чтобы узнать имя DLL-файла и путь.  
  
## <a name="see-also"></a>См. также  
 [Практическое: отладка машинных библиотек DLL](../debugger/how-to-debug-native-dlls.md)   
 [Практическое руководство. Использование окна модулей](../debugger/how-to-use-the-modules-window.md)






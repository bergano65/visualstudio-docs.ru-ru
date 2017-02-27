---
title: "Практическое руководство. Отладка элемента управления ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "отладка контейнеров элементов управления ActiveX [Visual Studio]"
  - "элементы управления ActiveX, отладка"
  - "контейнеры, указание для сеансов отладки"
  - "элементы управления с привязкой к данным, ActiveX"
  - "отладка элементов управления ActiveX"
  - "тестовый контейнер"
  - "проверка [Visual Studio], элементы управления ActiveX"
  - "проверка [Visual Studio], контейнеры тестов"
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Практическое руководство. Отладка элемента управления ActiveX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.  Чтобы изменить параметры, в меню "Сервис" выберите команду "Параметры импорта и экспорта".  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Чтобы выполнить отладку элемента управления ActiveX, задайте контейнер \(исполняемый файл\) для элемента управления.  
  
### Задание контейнера для сеанса отладки  
  
1.  Выберите проект в Обозревателе решений.  
  
2.  В меню **Вид** выберите **Страницы свойств**.  
  
3.  В диалоговом окне **Страницы свойств проекта** откройте папку **Свойства конфигурации** и выберите категорию **Отладка**.  
  
4.  В категории **Отладка** найдите свойство **Команда**.  
  
5.  Задайте путь к контейнеру.  Например, C:\\Program Files\\Internet Explorer\\IEXPLORE.EXE.  
  
6.  Если задать обозреватель Internet Explorer в качестве контейнера и использовать возможность Active Desktop, введите `/new` в поле **Аргументы команды**.  
  
7.  Нажмите кнопку **ОК**.  
  
     Если не задавать контейнер в диалоговом окне **Страницы свойств проекта**, его можно будет задать при запуске отладки.  При выборе команды запуска отладки появится диалоговое окно [Исполняемый файл для сеанса отладки](../debugger/executable-for-debugging-session-dialog-box.md).  Задайте в диалоговом окне путь к контейнеру.  
  
## См. также  
 [Элементы управления ActiveX](/visual-cpp/mfc/activex-controls)   
 [Тестирование свойств и событий с использованием тестового контейнера](/visual-cpp/mfc/testing-properties-and-events-with-test-container)   
 [Отладка COM и ActiveX](../debugger/com-and-activex-debugging.md)   
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)
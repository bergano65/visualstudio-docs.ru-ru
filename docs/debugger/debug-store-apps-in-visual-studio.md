---
title: "Отладка приложений Магазина в Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 48a85bcf-290b-4390-9993-f6f9dd73ad03
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Отладка приложений Магазина в Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Отладчик Visual Studio позволяет вам управлять выполнением программы и изучать ее состояние. Вы можете использовать отладчик, чтобы найти причину неполадок в приложении Магазина Windows и понять, как именно это приложение работает. Когда вы приостанавливаете выполнение в отладчике, Visual Studio отображает исходный файл, содержащий выполняемый код, и выделяет выполняемый оператор. Вы можете просмотреть значение переменных, стек вызовов выполняемых функций и другие аспекты состояния программы. Вы можете продолжить выполнение \(пошаговое\) программы по одному оператору за раз, чтобы определить, как именно операторы изменяют значения в программе. В приложениях на JavaScript вы можете просматривать и контролировать DOM на странице.  
  
## Содержание раздела  
  
|||  
|-|-|  
|[Запуск сеанса отладки \(JavaScript\)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)|В разделе "Запуск сеанса отладки" описываются различные варианты настройки и запуска сеанса отладки для приложения, написанного на JavaScript.|  
|[Управление выполнение в сессии отладки \(JavaScript\)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)|В разделе "Навигация по отладчику" приведено простое приложение, демонстрирующее, как запускать и останавливать отладку, осуществлять переходы по коду и просматривать состояние программы.|  
|[Краткое руководство по отладке HTML и CSS](../debugger/quickstart-debug-html-and-css.md)|В разделе "Отладка HTML и CSS" показано, как осуществлять интерактивную отладку приложения JavaScript с помощью инструментов проверки Live DOM для просмотра и изменения HTML и CSS.|  
|[Краткое руководство. Отладка JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)|В разделе "Отладка JavaScript с использованием консоли" показано, как осуществлять интерактивную отладку приложения JavaScript с использованием [Команды консоли JavaScript](../debugger/javascript-console-commands.md).|  
|[Запуск сеанса отладки \(VB, C\#, C\+\+ и XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)|В разделе "Запуск сеанса отладки \(Visual C\+\+, Visual C\# и Visual Basic\)" описываются различные варианты настройки и запуска сеанса отладки для приложения, написанного на Visual C\+\+, Visual C\# или Visual Basic.|  
|[Навигация по сеансу отладки \(XAML и C\#\)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)|В разделе "Навигация по отладчику" приведено простое приложение, демонстрирующее, как запускать и останавливать отладку, осуществлять переходы по коду, а также просматривать и изменять состояние программы.|  
|[Вызов событий приостановки, возобновления и фоновых событий для Магазина Windows](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)|Отладчик отключает события управления жизненным циклом процесса Windows, которые приостанавливают приложения, возобновляют и завершают их работу. Вы можете активировать эти события из панели инструментов отладчика.<br /><br /> Фоновые задачи позволяют выполнять важные операции, даже если приложение приостановлено. Отладчик позволяет вам запустить такую фоновую задачу и выполнить ее отладку.|  
  
## См. также  
 [Отладка в Visual Studio \(в библиотеке MSDN\)](http://go.microsoft.com/fwlink/?LinkID=226896)
---
title: "Отладка приложений UWP в Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 48a85bcf-290b-4390-9993-f6f9dd73ad03
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 8684a1220b871e2c77f8c0229cddd807a6031cd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debug-uwp-apps-in-visual-studio"></a>Отладка приложений UWP в Visual Studio
Отладчик Visual Studio позволяет вам управлять выполнением программы и изучать ее состояние. Чтобы найти причину неполадок в приложениях UWP и понять, как именно приложение работает, можно использовать отладчик. Когда вы приостанавливаете выполнение в отладчике, Visual Studio отображает исходный файл, содержащий выполняемый код, и выделяет выполняемый оператор. Вы можете просмотреть значение переменных, стек вызовов выполняемых функций и другие аспекты состояния программы. Вы можете продолжить выполнение (пошаговое) программы по одному оператору за раз, чтобы определить, как именно операторы изменяют значения в программе. В приложениях на JavaScript вы можете просмотреть и контролировать DOM на странице.  
  
## <a name="in-this-section"></a>Содержание раздела  
  
|||  
|-|-|  
|[Запуск сеанса отладки (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)|В разделе "Запуск сеанса отладки" описываются различные варианты настройки и запуска сеанса отладки для приложения, написанного на JavaScript.|  
|[Управление выполнение в сессии отладки (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)|В разделе "Навигация по отладчику" приведено простое приложение, демонстрирующее, как запускать и останавливать отладку, осуществлять переходы по коду и просматривать состояние программы.|  
|[Краткое руководство по отладке HTML и CSS](../debugger/quickstart-debug-html-and-css.md)|В разделе "Отладка HTML и CSS" показано, как осуществлять интерактивную отладку приложения JavaScript с помощью инструментов проверки Live DOM для просмотра и изменения HTML и CSS.|  
|[Краткое руководство: Отладка JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)|Отладка JavaScript с использованием консоли показано, как осуществлять интерактивную отладку приложения JavaScript с использованием [команды консоли JavaScript](../debugger/javascript-console-commands.md).|  
|[Запуск сеанса отладки (VB, C#, C++ и XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)|В разделе "Запуск сеанса отладки (Visual C++, Visual C# и Visual Basic)" описываются различные варианты настройки и запуска сеанса отладки для приложения, написанного на Visual C++, Visual C# или Visual Basic.|  
|[Навигация по сеансу отладки (Xaml и C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)|В разделе "Навигация по отладчику" приведено простое приложение, демонстрирующее, как запускать и останавливать отладку, осуществлять переходы по коду, а также просматривать и изменять состояние программы.|  
|[Активировать приостановки, возобновления и фоновых событий для приложений UWP)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)|Отладчик отключает события управления жизненным циклом процесса Windows, которые приостанавливают приложения, возобновляют и завершают их работу. Вы можете активировать эти события из панели инструментов отладчика.<br /><br /> Фоновые задачи позволяют выполнять важные операции, даже если приложение приостановлено. Отладчик позволяет вам запустить такую фоновую задачу и выполнить ее отладку.|  
  
## <a name="see-also"></a>См. также  
 [Отладка в Visual Studio](../debugger/index.md)  
 [Обзор возможностей отладчика (в библиотеке MSDN)](http://go.microsoft.com/fwlink/?LinkID=226896)
---
title: 'Практическое: отладка из проекта DLL | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 965a68194241c5e93e1da5bc6a9ba3f46db17213
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254791"
---
# <a name="how-to-debug-from-a-dll-project"></a>How to: Debug from a DLL Project
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы начать отладку проекта DLL, необходимо указать вызывающее приложение в свойствах проекта. Страницы свойств C++ отличаются по структуре и содержимому от страниц свойств C# и Visual Basic.  
  
 Если управляемая библиотека DLL вызывается машинным кодом и вы хотите отладить и то, и другое, это можно указать в свойствах проекта. Дополнительные сведения см. в разделе [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
>  Вы не можете указать внешнее вызывающее приложение в выпусках Express для Visual Studio. Вместо этого необходимо добавить проект исполняемого файла в решение, задать его в качестве запускаемого проекта и вызвать методы в библиотеке DLL из проекта исполняемого файла.  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Чтобы задать вызывающее приложение в проекте C++  
  
1.  Щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и выберите **свойства**. Перейдите к **Отладка** вкладки.  
  
2.  Убедитесь, что **конфигурации** поля в верхней части окна задается **Отладка**.  
  
3.  Перейдите к **свойства конфигурации / Отладка**.  
  
4.  В **отладчик для запуска** выберите **локальный отладчик Windows** или **удаленный отладчик Windows**.  
  
5.  В **команда** или **удаленной команды** , добавьте полный путь приложения.  
  
6.  Добавьте необходимые аргументы для **аргументы команды** поле.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Чтобы задать вызывающее приложение в проекте C# или Visual Basic  
  
1.  Щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и выберите **свойства**. Перейдите к **Отладка** вкладки.  
  
     Выберите **запуск внешней программы**и добавьте полный путь имя программы для запуска.  
  
     Если вам нужно добавить аргументы командной строки внешней программы, добавьте их в **аргументы командной строки** поля.  
  
2.  Вы можете также вызвать приложение как URL-адрес. (Это может понадобиться при отладке управляемой библиотеки DLL, используемой локальным приложением ASP.NET.)  
  
     В разделе **действие при запуске**выберите **запуск обозревателя в URL-адрес:** переключатель и укажите URL-адрес.  
  
### <a name="to-start-debugging-from-the-dll-project"></a>Чтобы запустить отладку из проекта DLL  
  
1.  Установите точки останова надлежащим образом.  
  
2.  Начать отладку (нажмите клавишу F5, щелкните зеленую стрелку или нажмите кнопку **отладка | начать отладку**).  
  
## <a name="see-also"></a>См. также  
 [Отладка проектов DLL](../debugger/debugging-dll-projects.md)   
 [Параметры проекта для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)




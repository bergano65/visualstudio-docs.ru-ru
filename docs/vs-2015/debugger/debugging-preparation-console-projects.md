---
title: 'Подготовка к отладке: проекты консоли | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ac87f6c5ef5fcf9fc7ca5532fe7436dedb8ba97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691219"
---
# <a name="debugging-preparation-console-projects"></a>Подготовка к отладке: консольные проекты
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Подготовка к отладке консольного проекта аналогична подготовке к отладке проекта Windows, с некоторыми дополнительными соображениями. Дополнительные сведения см. в разделе [приложений Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md), и [Подготовка к отладке: Приложения Windows Forms (.NET)](https://msdn.microsoft.com/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). Из-за схожести всех консольных приложений в этом разделе описываются следующие типы проектов:  
  
- консольное приложение C#;  
  
- консольное приложение Visual Basic;  
  
- консольное приложение C++ (.NET);  
  
- консольное приложение С++ (Win32).  
  
  Может потребоваться задание аргументов командной строки для консольного приложения. Дополнительные сведения см. в статьях [Параметры проектов для конфигураций отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md) и [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), или [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Подобно всем свойствам проекта, эти аргументы сохраняются в интервале между сеансами (как отладки, так и Visual Studio). Поэтому, если консольное приложение было ранее отлажено, помните, что в диалоговом окне ** \<Project> страницы свойств** могут быть аргументы из предыдущих сеансов.  
  
  Консольное приложение использует окно **Консоль** для получения входных данных и отображения выходных сообщений. Для записи в окно **Консоль** приложение должно использовать объект **Консоль** вместо объекта Debug. Для записи в окно **Вывод Visual Studio** используется, как обычно, объект Debug. Необходимо убедиться в какое место приложение записывает данные, иначе может оказаться, что поиск сообщений ведется не в том месте. Дополнительные сведения см. в разделах [Класс Console](https://msdn.microsoft.com/library/system.console.aspx), [Класс Debug](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) и [Окно вывода](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Запуск приложения  
 Некоторые консольные приложения после запуска выполняются до полного завершения, после чего сразу закрываются. Если это происходит быстро, то можно не успеть прервать выполнение приложения и выполнить отладку. Чтобы можно было выполнить отладку такого приложения, необходимо использовать один из следующих приемов для запуска приложения.  
  
- После запуска приложение выполняется до достижения точки останова.  
  
- После запуска выполнение приложения сразу же приостанавливается на первой строке исходного кода.  
  
- В окне исходного кода щелкните правой кнопкой мыши строку и выберите команду **выполнить до текущей позиции**.  
  
   После запуска приложение выполняется до достижения выделенной строки или до точки останова, если та встречается раньше.  
  
  При отладке консольного приложения может потребоваться запуск приложения из командной строки, а не из Visual Studio. В этом случае можно запустить приложение из командной строки и присоединить к нему отладчик Visual Studio. См. сведения о [присоединении к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  При запуске консольного приложения из Visual Studio окно **Консоль** иногда отображается позади окна Visual Studio. Если при попытке запустить консольное приложение из Visual Studio кажется, что ничего не происходит, попробуйте переместить окно Visual Studio.  
  
## <a name="see-also"></a>См. также:  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)   
 [Типы проектов Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Типы проектов C#, F # и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)

---
title: 'Подготовка к отладке: Консольные проекты | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29c54c4bfdeb0341270d78ce677b6085d6f159a2
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305186"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Подготовка к отладке: Консольные проекты (C#, C++, Visual Basic, F#)

Подготовка к отладке консольного проекта аналогична подготовке к отладке проекта Windows, с некоторыми дополнительными соображениями. Дополнительные сведения см. в разделе [приложений Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md), и [Подготовка к отладке: приложения Windows Forms (.NET)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)). Из-за схожести всех консольных приложений в этом разделе описываются следующие типы проектов:  
  
- C#, Visual Basic и F# консольное приложение  
  
- консольное приложение C++ (.NET);  
  
- консольное приложение С++ (Win32).  
  
  Может потребоваться задание аргументов командной строки для консольного приложения. Дополнительные сведения см. в разделе [параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), или [параметры проекта для C# отладки Конфигурации](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Подобно всем свойствам проекта, эти аргументы сохраняются в интервале между сеансами (как отладки, так и Visual Studio). Поэтому необходимо учитывать, что если предыдущий сеанс был посвящен отладке консольного приложения, в диалоговом окне **Страницы свойств \<проект>** могут присутствовать аргументы, сохранившиеся от предыдущих сеансов отладки.  
  
  Консольное приложение использует окно **Консоль** для получения входных данных и отображения выходных сообщений. Записываемый **консоли** окне приложение должно использовать **консоли** объекта вместо объекта Debug. Для записи в окно **Вывод Visual Studio** используется, как обычно, объект Debug. Необходимо убедиться в какое место приложение записывает данные, иначе может оказаться, что поиск сообщений ведется не в том месте. Дополнительные сведения см. в разделах [Класс Console](/dotnet/api/system.console), [Класс Debug](/dotnet/api/system.diagnostics.debug) и [Окно вывода](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Запуск приложения  
 Некоторые консольные приложения после запуска выполняются до полного завершения, после чего сразу закрываются. Если это происходит быстро, то можно не успеть прервать выполнение приложения и выполнить отладку. Чтобы можно было выполнить отладку такого приложения, необходимо использовать один из следующих приемов для запуска приложения.  
  
- Установите точку останова в коде и запустите приложение.
  
- Запуск приложения с помощью **F10** (**Отладка** > **шаг с обходом**) или **F11** (**Отладка**  >  **Шаг с заходом**), а затем просмотрите код, с помощью других параметров, таких как **выполнение до щелкнутого**.
  
- В редакторе кода, щелкните правой кнопкой мыши линию и выберите **выполнить до текущей позиции**.  
  
  При отладке консольного приложения может потребоваться запуск приложения из командной строки, а не из Visual Studio. В этом случае можно запустить приложение из командной строки и присоединить к нему отладчик Visual Studio. Дополнительные сведения см. в разделе [подключиться к процессам, под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  При запуске консольного приложения из Visual Studio окно **Консоль** иногда отображается позади окна Visual Studio. Если при попытке запустить консольное приложение из Visual Studio кажется, что ничего не происходит, попробуйте переместить окно Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)   
 [Типы проектов Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)
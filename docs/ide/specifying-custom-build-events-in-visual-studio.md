---
title: "Указание настраиваемых событий сборки в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: fd5955068a899199969c970434ff14401a654d35
ms.lasthandoff: 04/05/2017

---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Указание настраиваемых событий построения в Visual Studio
Указав пользовательское событие сборки, вы можете автоматически запустить команды перед тем, как сборка запустится или после того, как она завершится. Например, можно запустить BAT-файл до запуска сборки или скопировать новые файлы в папку после выполнения сборки. События сборки запускаются, только если сборка успешно достигает этих точек в процессе сборки.  
  
 Конкретные сведения об используемом языке программирования см. в следующих разделах:  
  
-   Visual Basic — [Практическое руководство. Указание событий сборки (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).  
  
-   Visual C# и F# — [Указание событий сборки (C#)](../ide/how-to-specify-build-events-csharp.md).  
  
-   Visual C++ — [Указание событий сборки ](/cpp/ide/specifying-build-events).  
  
## <a name="syntax"></a>Синтаксис  
 События сборки следуют тому же синтаксису, что и команды DOS, но для упрощения процесса создания событий сборки можно использовать макросы. Список доступных макросов см. в разделе [Диалоговое окно "Командная строка события перед сборкой" или "Командная строка события после сборки"](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
 Для улучшения результатов воспользуйтесь советами по форматированию:  
  
-   Добавьте оператор `call` перед всеми событиями сборки, запускающими BAT-файлы.  
  
     Пример: `call C:\MyFile.bat`  
  
     Пример: `call C:\MyFile.bat call C:\MyFile2.bat`  
  
-   Заключите пути к файлам в кавычки.  
  
     Пример (для [!INCLUDE[win8](../debugger/includes/win8_md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"  
  
-   Разделите несколько команд с помощью разрывов строк.  
  
-   При необходимости включите подстановочные знаки.  
  
     Пример: `for %I in (*.txt *.doc *.html) do copy %I c:\`*mydirectory*`\`  
  
    > [!NOTE]
    >  Команда `%I` в коде выше должна быть `%%I` в пакетных скриптах.  
  
## <a name="see-also"></a>См. также  
 [Компилирование и сборка](../ide/compiling-and-building-in-visual-studio.md)   
 [Диалоговое окно «Командная строка события "До сборки" или "После сборки"»](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Специальные знаки в MSBuild](../msbuild/msbuild-special-characters.md)   
 [Пошаговое руководство. Построение приложения](../ide/walkthrough-building-an-application.md)

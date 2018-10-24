---
title: Указание настраиваемых событий сборки в Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29273ff1580d7fcb757a979309d38f599a9ff499
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908747"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Указание настраиваемых событий сборки в Visual Studio

Указав пользовательское событие сборки, вы можете автоматически запустить команды перед тем, как сборка запустится или после того, как она завершится. Например, можно запустить *BAT*-файл до запуска сборки или скопировать новые файлы в папку после выполнения сборки. События сборки запускаются, только если сборка успешно достигает этих точек в процессе сборки.

 Конкретные сведения об используемом языке программирования см. в следующих разделах.

-   Visual Basic — [Практическое руководство. Указание событий сборки (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

-   C# и F# — [Указание событий сборки (C#)](../ide/how-to-specify-build-events-csharp.md).

-   Visual C++ — [Указание событий сборки](/cpp/ide/specifying-build-events).

## <a name="syntax"></a>Синтаксис

События сборки следуют тому же синтаксису, что и команды DOS, но для упрощения процесса создания событий сборки можно использовать макросы. Список доступных макросов см. в разделе [Диалоговое окно "Командная строка события перед сборкой" или "Командная строка события после сборки"](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

 Для улучшения результатов воспользуйтесь советами по форматированию:

- Добавьте оператор `call` перед всеми событиями сборки, запускающими *BAT*-файлы.

   Пример: `call C:\MyFile.bat`

   Пример: `call C:\MyFile.bat call C:\MyFile2.bat`

- Заключите пути к файлам в кавычки.

   Пример (для [!INCLUDE[win8](../debugger/includes/win8_md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"

- Разделите несколько команд с помощью разрывов строк.

- При необходимости включите подстановочные знаки.

   Пример: `for %I in (*.txt *.doc *.html) do copy %I c:\`*mydirectory*`\`

  > [!NOTE]
  >  Команда `%I` в коде выше должна быть `%%I` в пакетных скриптах.

## <a name="see-also"></a>См. также

- [Компиляция и сборка](../ide/compiling-and-building-in-visual-studio.md)
- [Диалоговое окно "Командная строка события перед сборкой" или "Командная строка события после сборки"](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Специальные знаки в MSBuild](../msbuild/msbuild-special-characters.md)
- [Пошаговое руководство. Сборка приложения](../ide/walkthrough-building-an-application.md)

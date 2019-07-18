---
title: Отладка с помощью JIT-отладчик | Документация Майкрософт
ms.date: 09/24/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2aff8e1b515f460e6fdc31a528e6730971b7853
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62853160"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Отладка с помощью JIT-отладчик в Visual Studio

Just-In-Time отладки Visual Studio можно запускать автоматически при приложения, запущенные вне Visual Studio ошибок или сбоев. С Just-In-Time отладки можно протестировать приложения, находящиеся вне Visual Studio и откройте Visual Studio, чтобы начать отладку при возникновении проблемы.

Отладка Just-In-Time работает для классических приложений Windows. Он не работает для универсальных приложений Windows, или для управляемого кода, который размещается в собственном приложении, например для визуализаторов.

> [!TIP]
> Если вы просто хотите остановить окно JIT – отладчик скрывается, но не установлена среда Visual Studio, см. в разделе [Отключить JIT – отладчик](../debugger/just-in-time-debugging-in-visual-studio.md). Если у вас один раз было установлено приложение Visual Studio, может потребоваться [отключение Just-In-Time отладки из реестра Windows](#disable-just-in-time-debugging-from-the-windows-registry).

## <a name="BKMK_Enabling"></a> Включить или отключить Just-In-Time отладки в Visual Studio

>[!NOTE]
>Чтобы включить или отключить Just-In-Time отладки, необходимо использовать Visual Studio с правами администратора. Включение или отключение Just-In-Time отладки устанавливает раздел реестра, а также могут потребоваться права администратора для изменения этого ключа. Чтобы открыть Visual Studio с правами администратора, щелкните правой кнопкой мыши приложение Visual Studio и выберите **Запуск от имени администратора**.

Можно настроить Just-In-Time отладки из Visual Studio **средства** > **параметры** (или **Отладка** > **параметры**) диалоговое окно.

**Включение или отключение JIT–отладки**

1. На **средства** или **Отладка** меню, выберите **параметры** > **Отладка**  >   **Just-In-Time**.

   ![Включение или отключение JIT-отладка](../debugger/media/dbg-jit-enable-or-disable.png "Включение или отключение JIT-отладка")

1. В **включить JIT-отладку для следующих типов кода** выберите типы кода, требуется Just-In-Time отладки для отладки: **Управляемые**, **собственного**, и/или **скрипт**.

1. Нажмите кнопку **ОК**.

При включении Just-In-Time отладчик, но она не открывается, когда происходит сбой приложения или ошибки, см. в разделе [Устранение неполадок с JIT-отладка](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Отключить Just-In-Time отладки из реестра Windows

JIT-отладка может оставаться включенной даже после удаления Visual Studio с компьютера. Если больше не установлена среда Visual Studio, вы можете отключить Just-In-Time отладки путем редактирования реестра Windows.

**Отключение JIT-отладки путем редактирования реестра**

1. Из Windows **запустить** меню **редактора реестра** (*regedit.exe*).

2. В **редактора реестра** окна, найдите и удалите следующие записи реестра:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Раздел реестра JIT](../debugger/media/dbg-jit-registry.png "раздел реестра JIT")

3. Если компьютер работает под управлением 64-разрядной операционной системе, также удалите следующие записи реестра:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Убедитесь, что не удалить или изменить разделы реестра.

5. Закрыть **редактора реестра** окна.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Включить Just-In-Time отладка формы Windows

По умолчанию формы Windows приложения имеют обработчик исключений верхнего уровня, который позволяет приложению продолжать работать, если его можно восстановить. Если в приложении Windows Forms вызывает необработанное исключение, отобразится следующее диалоговое окно:

![Форма Windows необработанное исключение](../debugger/media/windowsformsunhandledexception.png "формы Windows необработанное исключение")

Чтобы включить Just-In-Time отладку вместо обработки стандартных ошибок формы Windows, добавьте эти параметры:

- В `system.windows.forms` раздел *machine.config* или  *\<имя_приложения >. exe.config* файле `jitDebugging` значение `true`:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- В приложении C++ Windows Form, следует также установить `DebuggableAttribute` для `true` в *.config* файл или в собственном коде. Если компиляция выполняется с атрибутом [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format), но без [/Og](/cpp/build/reference/og-global-optimizations), компилятор автоматически задаст этот атрибут. Если требуется отладка построения выпуска неоптимизированных, тем не менее, необходимо задать `DebuggableAttribute` , добавив следующую строку в вашем приложении *AssemblyInfo.cpp* файла:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Дополнительные сведения см. в разделе <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="BKMK_Using_JIT"></a>Использовать Just-In-Time отладки
В этом примере описывается Just-In-Time отладки, когда приложение выдает ошибку.

- Необходимо иметь Visual Studio не установлена, выполните следующие действия. Если у вас нет Visual Studio, вы можете скачать бесплатный [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

- Убедитесь, что Just-In-Time Отладка [включена](#BKMK_Enabling) в **средства** > **параметры** > **Отладка**  >  **Just-In-Time**.

В этом примере вам предстоит C# консольное приложение в Visual Studio, который создает [NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. В Visual Studio создайте C# консольное приложение (**файл** > **New** > **проекта** > **Visual C#**   >  **Консольное приложение**) с именем *ThrowsNullException*. Дополнительные сведения о создании проектов в Visual Studio, см. в разделе [Пошаговое руководство: Создание простого приложения](/visualstudio/get-started/csharp/tutorial-wpf).

1. Открыв проект в Visual Studio, откройте *Program.cs* файл. Замените метод Main() следующий код, который выводит на консоль строку и затем создает исключение NullReferenceException:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Чтобы построить решение, выберите значок **Отладка** (по умолчанию) или **выпуска** конфигурации, а затем выберите **построения** > **Перестроить решение** .

   > [!NOTE]
   > - Выберите **Отладка** конфигурацию для полным набором функций отладки.
   > - При выборе [выпуска](../debugger/how-to-set-debug-and-release-configurations.md) конфигурации, необходимо отключить [Just My Code](../debugger/just-my-code.md) для работы этой процедуры. В разделе **средства** > **параметры** > **Отладка**, отмените выбор **включить только мой код**.

   Дополнительные сведения о конфигурациях сборки см. в разделе [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).

1. Откройте приложение построенный *ThrowsNullException.exe* в вашей C# папку проекта (*...\ThrowsNullException\ThrowsNullException\bin\Debug* или *...\ThrowsNullException\ ThrowsNullException\bin\Release*).

   Вы должны увидеть следующее командное окно:

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. **Выберите JIT – отладчик** откроется диалоговое окно.

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   В разделе **доступных отладчиков**выберите **новый экземпляр \<вашей основной версии или выпуска Visual Studio >**, если он еще не выбран.

1. Нажмите кнопку **ОК**.

   В новом экземпляре Visual Studio откроется проект ThrowsNullException выполнение остановится на строке, который вызвал исключение:

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

Можно начать отладку на этом этапе. При отладке реальное приложение, необходимо узнать, почему код было вызвано исключение.

> [!CAUTION]
> Если приложение содержит код без доверия, появится диалоговое окно предупреждения безопасности, что позволяет решить, следует ли продолжать отладку. Перед продолжением отладки решите, доверяете ли вы код. Этот код написан вами самостоятельно? Если приложение выполняется на удаленном компьютере, узнаете ли вы имя процесса? Если приложение выполняется локально, учитывайте возможность выполнения вредоносного кода на компьютере. Если код является доверенной, выберите **ОК**. В противном случае нажмите кнопку **Отмена**.

## <a name="jit_errors"></a> Устранение неполадок Just-In-Time отладки

Если Just-In-Time отладка не начинается при аварийном завершении приложения, несмотря на то, что он включен в Visual Studio:

- Отчеты об ошибках Windows может досталось обработки ошибок на компьютере.

  Чтобы устранить эту проблему, используйте редактор реестра, чтобы добавить **значение DWORD** из **отключено**, с помощью **значение** из **1**, в следующие разделы реестра:

  - **Отчеты об ошибках HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows**

  - (Для 64-разрядных компьютеров). **Отчеты об ошибках HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows**

  Дополнительные сведения см. в разделе [. Параметры отчетов об ошибках Windows](https://docs.microsoft.com/windows/desktop/wer/wer-settings).

- Известная проблема Windows может быть причиной Just-In-Time отладчик, переход на другой.

  Исправление является добавление **значение DWORD** из **автоматически**, с помощью **данные значения** из **1**, в следующие разделы реестра:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Для 64-разрядных компьютеров). **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Может появиться следующие сообщения об ошибках во время Just-In-Time отладки:

- **Не удалось подключиться к аварийному процессу. Указанная программа не является программой Windows или MS–DOS.**

    Отладчик попытался подключиться к процессу, под управлением другого пользователя.

    Чтобы решить эту проблему, в Visual Studio откройте **Отладка** > **присоединение к процессу**и найдите процесс, необходимо выполнить отладку в **доступные процессы** список. Если вы не знаете имя процесса, найти идентификатор процесса в **JIT – отладчик Visual Studio** диалоговое окно. Выберите процесс в **доступные процессы** и выберите **Attach**. Выберите **нет** отклонить Just-In-Time диалоговое окно отладчика.

- **Не удалось запустить отладчик, так как пользователь не вошел в систему.**

    Нет пользователей, вошедших в консоль, поэтому отсутствует сеанс пользователя для отображения Just-In-Time отладка диалогового окна.

    Для решения этой проблемы необходимо войти в компьютер.

- **Класс не зарегистрирован.**

    Отладчик пытался создать класс COM, который не зарегистрирован, вероятно, из-за проблем с установкой.

    Чтобы устранить эту проблему, используйте установщик Visual Studio для переустановки или восстановления установки Visual Studio.

## <a name="see-also"></a>См. также

- [Безопасность отладчика](../debugger/debugger-security.md)
- [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)
- [Параметры, отладка, Just-In-Time диалоговое окно](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Предупреждение системы безопасности. Подключение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если следующие сведения не вызывают доверия, то не следует присоединяться к процессу](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)

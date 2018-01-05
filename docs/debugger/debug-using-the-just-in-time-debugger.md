---
title: "Отладка с помощью JIT-отладчик | Документы Microsoft"
ms.custom: 
ms.date: 07/06/17
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
caps.latest.revision: "48"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4bcdd28247b767321d3d5fed9681082538ba2b12
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Отладка с помощью JIT-отладчик в Visual Studio
Just-In-Time отладка автоматически запускает Visual Studio при возникновении исключения или неустранимой ошибки в программе, на котором выполняется вне Visual Studio. Это позволяет тестировать приложение, не запуская Visual Studio и начинать отладку в Visual Studio при возникновении проблемы.

Отладка в времени работает для классических приложений Windows. Не работает для универсальных приложений Windows, а не работает для управляемого кода, размещенного в приложении машинного кода, например для визуализаторов.

> [!TIP] 
> Если требуется узнать, как реагировать на только время диалоговое окно отладчика см. в разделе [в этом разделе](../debugger/just-in-time-debugging-in-visual-studio.md).

##  <a name="BKMK_Enabling"></a>Включение или отключение непосредственно в время отладки  
Можно включить или отключить непосредственно времени отладки из Visual Studio **Сервис > Параметры** диалоговое окно.
  
#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Включение или отключение JIT–отладки  
  
1.  Откройте Visual Studio с правами администратора (щелкните правой кнопкой мыши и выберите **Запуск от имени администратора**).

    Включение или отключение времени непосредственно отладки устанавливает раздел реестра и правами администратора может потребоваться изменить этот ключ.
    
2. В меню **Сервис** выберите пункт **Параметры**.
  
2.  В **параметры** диалогового окна разверните **Отладка** узла.  
  
3.  В **Отладка** выберите **непосредственно в момент**.

    ![Включение или отключение JIT-отладка](../debugger/media/dbg-jit-enable-or-disable.png "Включение или отключение JIT-отладка") 
  
4.  В **включить JIT – отладку для следующих типов кода** установите или снимите соответствующих типов программ: **управляемое**, **собственного**, или **сценария**.    
  
5.  Нажмите кнопку **ОК**.  
  
JIT-отладка может оставаться включенной даже после удаления Visual Studio с компьютера. Если Visual Studio не установлен, невозможно отключить непосредственно времени отладки из Visual Studio **параметры** диалоговое окно. В таком случае JIT-отладку можно отключить, отредактировав реестр Windows.  
  
#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Отключение JIT-отладки путем редактирования реестра  
  
1.  На **запустить** меню, найдите и запустите`regedit.exe`  
  
2.  В **редактора реестра** окна, найдите и удалите следующие параметры реестра:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   Реестр\.NETFramework\DbgManagedDebugger  

    ![Раздел реестра JIT](../debugger/media/dbg-jit-registry.png "JIT реестра") 
  
3.  Если компьютер работает под управлением 64-разрядной операционной системе, также удалите следующие параметры реестра:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger  
  
4.  Будьте внимательны, чтобы случайно не удалить или не изменить какие-либо другие разделы реестра.  
  
5.  Закрыть **редактора реестра** окна.   
  
#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Включение JIT-отладки для приложений Windows Forms  
  
1.  По умолчанию для приложений Windows Forms имеется обработчик исключений верхнего уровня, позволяющий программе продолжать работу, если возможно восстановление после ошибки. Например если приложение Windows Forms вызывает необработанное исключение, вы увидите диалоговое окно следующим образом:  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     Для включения только по требованию отладки для приложения Windows Forms, необходимо выполнить следующие дополнительные действия:  
  
2.  Задать `jitDebugging` значение `true` в `system.windows.form` раздел machine.config или  *\<имя приложения >*. exe.config файла:  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  Для приложений Windows Form, написанных на языке C++, в файле CONFIG или в коде должен быть задан атрибут `DebuggableAttribute`. Если компиляция выполняется с [/ZI](/cpp/build/reference/z7-zi-zi-debug-information-format) и без [/Og](/cpp/build/reference/og-global-optimizations), компилятор сам задаст этот атрибут. Однако если требуется отладка неоптимизированного построения выпуска, этот атрибут необходимо задать самостоятельно. Для этого добавьте следующую строку в файл AssemblyInfo.cpp своего приложения:  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Дополнительные сведения см. в разделе <xref:System.Diagnostics.DebuggableAttribute>.  
  
## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Используйте отладку Just-In-Time  
 В этом разделе показано, что происходит, когда исполняемый файл создает исключение.  
  
 Необходимо иметь среда Visual Studio выполните следующие действия. Если у вас нет Visual Studio, вы можете загрузить бесплатную [Visual Studio Community Edition](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).  
  
 Убедитесь, что только время Отладка — это [включен](#BKMK_Enabling).
  
 В целях этого раздела мы выполним консольное приложение C# в Visual Studio, которая создает исключение [NullReferenceException](http://msdn.microsoft.com/Library/658af786-d893-4114-a3c5-31c7d586056a).  
  
 В Visual Studio, создайте консольное приложение C# (**файл > Создать > проект > Visual C# > консольное приложение**) с именем **ThrowsNullException**. Дополнительные сведения о создании проектов в Visual Studio см. в разделе [Пошаговое руководство: создание простого приложения](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).  
  
 При открытии проекта в Visual Studio откройте файл Program.cs. Замените метод Main() на следующий код, который выводит на консоль строку и затем создает исключение NullReferenceException:  
  
```csharp  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  В этой процедуры для работы в [конфигурации выпуска](../debugger/how-to-set-debug-and-release-configurations.md), необходимо отключить [только мой код](../debugger/just-my-code.md). В Visual Studio щелкните **Сервис > Параметры**. В **параметры** диалогового окна выберите **Отладка**. Удалить проверку из **включить только мой код**.  
  
 Выполните сборку решения (в Visual Studio выберите **сборки > Перестроить решение**). Можно выбрать отладки или конфигурации выпуска (выберите **отладки** для полного отладку). Дополнительные сведения о конфигурациях сборки см. в разделе [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).  
  
 Процесс построения создает исполняемый файл ThrowsNullException.exe. Его можно найти в папке, в котором создается проект C#: **...\ThrowsNullException\ThrowsNullException\bin\Debug** или **...\ThrowsNullException\ThrowsNullException\bin\Release**.  
  
 Дважды щелкните ThrowsNullException.exe. Появится окно командной строки следующим образом:  
  
 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")  
  
 Через несколько секунд откроется окно сообщений об ошибке:  
  
 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")  
  
 Не нажимайте кнопку **отменить**! Через несколько секунд вы увидите две кнопки **отладки** и **закрыть программу**. Нажмите кнопку **отладки**.  
  
> [!CAUTION]
>  Если приложение содержит ненадежный код, появится диалоговое окно с предупреждением системы безопасности. Это диалоговое окно позволяет выбрать, следует ли продолжать отладку или нет. Перед продолжением отладки решите, доверяете ли вы данному коду. Этот код написан вами самостоятельно? Доверяете ли вы автору кода? Если приложение выполняется на удаленном компьютере, узнаете ли вы имя процесса? Даже если приложение выполняется на локальном компьютере, это не обязательно означает, что ему можно доверять. Учитывайте возможность выполнения вредоносного кода на вашем компьютере. Если вы решите, что код вы собираетесь отладки доверять, нажмите **отладки**. В противном случае нажмите кнопку **не отлаживать**.  
  
 **JIT – отладчик Visual Studio** появится окно:  
  
 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")  
  
 В разделе **Доступные отладчики**, вы должны увидеть **новый экземпляр Microsoft Visual Studio <available version>**  выбрана строка. Если он не уже выбрана, выберите его.  
  
 В нижней части окна в разделе **требуется отлаживать, используя выбранный отладчик?**, нажмите кнопку **Да**.  
  
 ThrowsNullException проект откроется в новом экземпляре Visual Studio с Выполнение остановлено на строке, в которой создается исключение:  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 Можно начать отладку на этом этапе. Если бы это был реальному приложению, необходимо определить, почему код которой было вызвано исключение.  
  
## <a name="just-in-time-debugging-errors"></a>Ошибки JIT-отладки  
 Если вы не видите диалоговое окно при аварийном завершении программы, это возможно из-за параметров отчетов об ошибках Windows на компьютере. Дополнительные сведения см. в разделе [. Параметры отчетов об ошибках Windows](/windows-hardware/drivers/dashboard/windows-error-reporting-getting-started).  
  
 Могут отображаться следующие сообщения об ошибках, связанные с JIT–отладкой.  
  
-   **Не удается присоединиться к аварийному процессу. Указанная программа не является программой Windows или MS-DOS.**  
  
     Эта ошибка возникает при попытке подключиться к процессу, запущенного от имени другого пользователя.  
  
     Чтобы решить эту проблему, запустите Visual Studio откройте **присоединиться к процессу** диалогового окна **отладки** меню и найдите процесс, который нужно отладить в **доступные процессы**список. Если вы не знаете имя процесса, посмотрите **JIT – отладчик Visual Studio** диалоговое окно и запомните идентификатор процесса Выберите процесс в **доступные процессы** списке и нажмите кнопку **присоединение**. В **JIT – отладчик Visual Studio** диалоговое окно, нажмите кнопку **нет** чтобы закрыть диалоговое окно.  
  
-   **Не удалось запустить отладчик, поскольку пользователь не вошел в систему.**  
  
     Данная ошибка возникает, когда JIT–отладка пытается запустить Visual Studio на компьютере, на котором нет пользователей, вошедших в консоль. Так как пользователи, выполнившие вход, отсутствуют, также отсутствует сеанс пользователя, в котором следовало бы отображать диалоговое окно JIT–отладки.  
  
     Для решения этой проблемы необходимо войти в компьютер.  
  
-   **Класс не зарегистрирован.**  
  
     Эта ошибка указывает, что отладчик пытался создать класс COM, который не зарегистрирован, вероятно, из–за проблем с установкой.  
  
     Чтобы решить эту проблему, используйте установочный диск для переустановки или восстановления установки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Основы отладки](../debugger/debugger-basics.md)   
 [Just-In-Time, отладка, диалоговое окно параметров](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [Предупреждение безопасности. Присоединение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если следующие сведения не вызывают доверия, то не следует присоединяться к процессу](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)
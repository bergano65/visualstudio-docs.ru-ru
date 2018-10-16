---
title: 'Пошаговое руководство: Отладка в Windows Forms | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5fdd9dadc92143fabfaeea35d776b57b4b4c1748
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468534"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Пример. Отладка в Windows Forms
Форма Windows Forms — один из наиболее распространенных вариантов управляемых приложений. На основе формы Windows Forms создается стандартное приложение Windows. Можно реализовать данный примере на Visual Basic, C# или C++.  
  
 Для начала необходимо закрыть и открыть решения.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Чтобы подготовиться к выполнению данного пошагового руководства  
  
-   Если какое–либо решение уже открыто, закройте его. (На **файл** меню, выберите **закрыть решение**.)  
  
## <a name="create-a-new-windows-form"></a>Создание новой формы Windows Forms.  
 Далее нам предстоит создать новую форму Windows Forms.  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Чтобы создать форму Windows Forms для данного примера  
  
1.  На **файл** меню, выберите **New** и нажмите кнопку **проекта**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
2.  В области типов проектов, откройте **Visual Basic**, **Visual C#**, или **Visual C++** узел, затем  
  
    1.  Для Visual Basic или Visual C#, выберите **Windows Desktop** > **приложение формы Windows**.  
  
    2.  Visual C++ выберите **классическое приложение Windows**.  
  
3.  В **имя** окне укажите уникальное имя (например, Walkthrough_SimpleDebug) проекта.  
  
4.  Нажмите кнопку **ОК**.  
  
     Visual Studio создаст новый проект и откроет новую форму в конструкторе Windows Forms. Дополнительные сведения см. в разделе [конструктор Windows Forms](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
5.  На **представление** меню, выберите **элементов**.  
  
     Откроется Панель элементов. См. дополнительные сведения о [панели элементов](../ide/reference/toolbox.md).  
  
6.  В области элементов щелкните **кнопку** управления и перетащите его на поверхность разработки формы. Сбросьте кнопку в форму.  
  
7.  В области элементов щелкните **TextBox** управления и перетащите его на поверхность разработки формы. DROP **TextBox** в форме.  
  
8. На поверхности разработки формы дважды щелкните кнопку.  
  
     Появится страница кода. Курсор должен находиться в тексте `button1_Click`  
  
10. В функции `button1_Click` добавьте следующий код:  
  
    ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. В меню **Сборка** выберите команду **Собрать решение**.  
  
     Проект должен быть построен без ошибок.  
  
## <a name="debug-your-form"></a>Отладка формы  
 Теперь все готово для того, чтобы начать отладку.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Чтобы выполнить отладку формы Windows Forms, созданной для данного примера  
  
1.  В окне исходного кода щелкните левое поле на той же строке, в которую добавляется текст:  
  
     ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";  
    ``` 
  
     Появится красная точка, и текст строки будет выделен красным цветом. Красная точка представляет точку останова. Дополнительные сведения см. в разделе [точки останова](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583). Если приложение запускается из отладчика, выполнение этого приложения будет приостановлено отладчиком на строке с помеченным кодом. После этого можно просмотреть состояние приложения и произвести его отладку.  
  
    > [!NOTE]
    >  Щелкните правой кнопкой мыши любую строку кода, пункты **точки останова**, а затем нажмите кнопку **вставить точку останова** добавьте точку останова в этой строке.  
  
2.  ON **Отладка** меню, выберите **запустить**.  
  
     Запустится форма Windows Forms.  
  
3.  В форме Windows Forms щелкните добавленную кнопку.  
  
     После этого в Visual Studio приложение остановится на той строке, где была задана точка останова на странице кода. Эта строка будет выделена желтым цветом. Теперь можно просматривать переменные в приложении и управлять его выполнением. В этот момент приложение остановит свое выполнение и будет ожидать действий со стороны пользователя.  
  
4.  На **Отладка** меню, выберите **Windows**, затем **Watch**и нажмите кнопку **Контрольные значения 1**.  
  
5.  В **Контрольные значения 1** окно, щелкните пустую строку. В **имя** столбец, тип `textBox1.Text` (Если вы используете Visual Basic или Visual C#) или `textBox1->Text` (если используется C++), затем нажмите клавишу ВВОД.  
  
     **Контрольные значения 1** окно показывает значение этой переменной в двойных кавычках, как:  
  
    `""`  
 
6.  На **Отладка** меню, выберите **шаг с заходом**.  
  
     Значение textBox1.Text в **Контрольные значения 1** окно, чтобы:  
  
    `Button was clicked!`  
  
7.  На **Отладка** меню, выберите **Продолжить** для возобновления отладки программы.  
  
8.  В форме Windows Forms снова нажмите кнопку.  
  
     Visual Studio снова приостановит выполнение программы.  
  
9. Щелкните красную точка, представляющую точка останова.  
  
     Это действие удалит точка останова из кода программы.  
  
10. На **Отладка** меню, выберите **остановить отладку**.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Присоединение к приложению Windows Form для отладки  
 В [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] можно присоединить отладчик к выполняющемуся процессу. Если используется экспресс-выпуск, эта возможность не поддерживается.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Присоединение к приложению Windows Form для отладки  
  
1.  В созданном ранее проекте щелкните левое поле, чтобы еще раз установить точка останова на добавленной строке:  
  
     ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";   
  
2.  On the **Debug** menu, select **Start Without Debugging**.  
  
     The Windows Form starts running under Windows, just as if you had double-clicked its executable. The debugger is not attached.  
  
3.  On the **Debug** menu, select **Attach to Process**. (This command is also available on the **Tools** menu.)  
  
     The **Attach to Process** dialog box appears.  
  
4.  In the **Available Processes** pane, find the process name (Walkthrough_SimpleDebug.exe) in the **Process** column and click it.  
  
5.  Click the **Attach** button.  
  
6.  In your Windows Form, click the one and only button.  
  
     The debugger breaks execution of the Windows Form at the breakpoint.  
  
## See Also  
 [Debugging Managed Code](../debugger/debugging-managed-code.md)   
 [Debugger Security](../debugger/debugger-security.md)
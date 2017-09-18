---
title: "Расширение строки состояния | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "строки состояния, сведения о строках состояния"
  - "строки состояния, общие сведения"
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Расширение строки состояния
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Строка состояния Visual Studio в нижней части интегрированной среды разработки можно использовать для отображения информации.  
  
 При расширении строка состояния может отображать сведения и пользовательского интерфейса в четыре области: область отзывов, индикатор, область анимации и область конструктора. Региона обратной связи позволяет отображать текст и выделите текст. Индикатор показывает хода для краткосрочных операции, такие как сохранение файла. Область анимации отображает постоянно зациклен анимации, длительные операции или операции неопределенные длины, такие как построение нескольких проектов в решении. И область конструктора номер строки и столбца до текущего положения курсора.  
  
 В строке состояния можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> интерфейса \(из <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> службы\). Кроме того, любой объект, размещенные на фрейм окна можно зарегистрировать как строка клиентский объект состояния, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> интерфейса. При активации окна Visual Studio запрашивает у объекта, находящегося в этом окне для `IVsStatusbarUser` интерфейса. Если найден, он вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метод на возвращенный интерфейс и объект можно обновить в строке состояния в этом методе. Документирование windows, например, можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метод для обновления сведений в области конструктора, когда они становятся активными.  
  
 В следующих процедурах предполагается, что вы знаете, как создавать проект VSIX и добавлять команды пользовательского меню. Сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).\)  
  
## Изменение строки состояния  
 Эта процедура показано, как задать и получить текст, отображения статического текста и выделите текст отображается в области отзывы в строке состояния.  
  
#### Чтение и запись в строке состояния  
  
1.  Создайте проект VSIX с именем **TestStatusBarExtension** и добавить команду меню с именем **TestStatusBarCommand**.  
  
2.  В TestStatusBarCommand.cs замените код метода обработчика команды \(MenuItemCallback\) следующие:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Make sure the status bar is not frozen  
        int frozen;  
  
        statusBar.IsFrozen(out frozen);  
  
        if (frozen != 0)   
        {  
            statusBar.FreezeOutput(0);  
        }  
  
        // Set the status bar text and make its display static.  
        statusBar.SetText("We just wrote to the status bar.");  
  
        // Freeze the status bar.  
        statusBar.FreezeOutput(1);  
  
        // Get the status bar text.   
        string text;  
        statusBar.GetText(out text);  
        System.Windows.Forms.MessageBox.Show(text);  
  
        // Clear the status bar text.  
        statusBar.FreezeOutput(0);  
        statusBar.Clear();  
    }  
    ```  
  
3.  Скомпилируйте код и запустить отладку.  
  
4.  Откройте **средства** меню в экспериментальном экземпляре Visual Studio. Щелкните **вызова TestStatusBarCommand** кнопки.  
  
     Вы должны увидеть текст в строке теперь чтения состояния **«Мы только что записал панели состояния»** и в появившемся сообщении имеет тот же текст.  
  
#### Обновление индикатора хода выполнения  
  
1.  В этой процедуре будет показано, как инициализировать и обновлять индикатор хода выполнения.  
  
2.  Откройте файл TestStatusBarCommand.cs и замените метод MenuItemCallback следующим кодом:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
        uint cookie = 0;  
        string label = "Writing to the progress bar";  
  
        // Initialize the progress bar.  
        statusBar.Progress(ref cookie, 1, "", 0, 0);  
  
        for (uint i = 0, total = 20; i <= total; i++)  
        {  
            // Display progress every second.  
            statusBar.Progress(ref cookie, 1, label, i, total);  
            System.Threading.Thread.Sleep(1000);  
        }  
  
        // Clear the progress bar.  
        statusBar.Progress(ref cookie, 0, "", 0, 0);  
    }  
    ```  
  
3.  Скомпилируйте код и запустить отладку.  
  
4.  Откройте **средства** меню в экспериментальном экземпляре Visual Studio. Щелкните **вызова TestStatusBarCommand** кнопки.  
  
     Вы должны увидеть текст в строке теперь чтения состояния **«Записи индикатора выполнения.»** Вы также увидите индикатор обновляется каждую секунду в течение 20 секунд. После этого строка состояния индикатора очищаются.  
  
#### Отображение анимации  
  
1.  В строке состояния отображается цикла анимации, которая указывает либо длительной операции \(например, построение нескольких проектов в решении\). Если эта анимация не отображается, убедитесь, что указан правильный **инструменты и параметры** параметры:  
  
     Последовательно выберите пункты **Сервис\/Параметры \/ Общие** вкладку и снимите флажок **автоматически регулировать изображение в соответствии с производительностью клиента**. Затем установите флажок вложенных **Включить расширенное визуальное представление клиента**. Теперь вы сможете просмотреть анимацию при построении проекта в экспериментальном экземпляре Visual Studio.  
  
     В этой процедуре мы отображения стандартных анимации Visual Studio, который представляет создание проекта или решения.  
  
2.  Откройте файл TestStatusBarCommand.cs и замените метод MenuItemCallback следующим кодом:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Use the standard Visual Studio icon for building.  
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;  
  
        // Display the icon in the Animation region.  
        statusBar.Animation(1, ref icon);  
  
        // The message box pauses execution for you to look at the animation.  
        System.Windows.Forms.MessageBox.Show("showing?");  
  
        // Stop the animation.   
        statusBar.Animation(0, ref icon);  
    }  
    ```  
  
3.  Скомпилируйте код и запустить отладку.  
  
4.  Откройте **средства** в экспериментальном экземпляре Visual Studio и щелкните меню **вызова TestStatusBarCommand**.  
  
     Когда появится окно сообщения, вы увидите также анимации в строке состояния в правом углу. Если закрыть окно сообщения, исчезает анимации.
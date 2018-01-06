---
title: "Расширение в строке состояния | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cb8ea7f78b964ee828993c09e59af5b5e83fd031
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-status-bar"></a>Расширение в строке состояния
Для отображения сведений в нижней части интегрированной среды разработки можно использовать в строке состояния Visual Studio.  
  
 При расширении строка состояния может отображать сведения и пользовательского интерфейса в четыре области: область обратной связи, индикатор выполнения, область анимации и область конструктора. Область обратной связи позволяет отображать текст и выделить отображаемого текста. Индикатор выполнения показывает хода выполнения для краткосрочных операции, такие как сохранение файла. Область анимации отображает постоянно зациклен анимации длительные операции или неопределенные длины, например построение нескольких проектов в решении. И область конструктора отображает номер строки и столбца положения курсора.  
  
 В строке состояния можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> интерфейса (из <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> службы). Кроме того, любой объект, размещенные на фрейм окна можно зарегистрировать как строка клиентский объект состояния, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> интерфейса. Каждый раз, когда окно активируется, Visual Studio запрашивает у объекта, находящегося в этом окне для `IVsStatusbarUser` интерфейса. Если найден, он вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метод на возвращенный интерфейс и объект можно обновить в строке состояния в этом методе. Документирование windows, например, можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метод для обновления данных в область конструктора, когда они становятся активными.  
  
 В следующих процедурах предполагается понимания принципов создайте проект VSIX и добавьте пользовательские команды. Сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Изменение строки состояния  
 Эта процедура показано, как задать и получить текст, отображения статического текста и выделите текст отображается в области обратной связи в строке состояния.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Чтение и запись в строке состояния  
  
1.  Создайте проект VSIX с именем **TestStatusBarExtension** и добавьте команду меню с именем **TestStatusBarCommand**.  
  
2.  В TestStatusBarCommand.cs замените код метода обработчика команд (MenuItemCallback) с помощью следующего:  
  
    ```csharp  
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
  
3.  Скомпилируйте код и начните отладку.  
  
4.  Откройте **средства** меню в экспериментальном экземпляре Visual Studio. Нажмите кнопку **TestStatusBarCommand вызова** кнопки.  
  
     Вы должны увидеть текст в строке теперь чтение состояния **«Мы только что написанный в строке состояния.»** и в появившемся окне сообщения имеет тот же текст.  
  
#### <a name="updating-the-progress-bar"></a>Обновление индикатора хода выполнения  
  
1.  В этой процедуре будет показано, как инициализировать и обновление индикатора хода выполнения.  
  
2.  Откройте файл TestStatusBarCommand.cs и замените метод MenuItemCallback следующим кодом:  
  
    ```csharp  
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
  
3.  Скомпилируйте код и начните отладку.  
  
4.  Откройте **средства** меню в экспериментальном экземпляре Visual Studio. Нажмите кнопку **TestStatusBarCommand вызова** кнопки.  
  
     Вы должны увидеть текст в строке теперь чтение состояния **«Запись индикатор выполнения».** Вы также увидите обновляются каждую секунду в течение 20 секунд индикатор выполнения. После этого в строке состояния индикатора очищаются.  
  
#### <a name="displaying-an-animation"></a>Отображение анимации  
  
1.  В строке состояния отображается цикла анимации, которая указывает либо длительную операцию (например, построение нескольких проектов в решении). Если вы не видите данной анимации, убедитесь, что у вас есть правильный **Сервис / Параметры** параметры:  
  
     Последовательно выберите пункты **Сервис/Параметры / Общие** вкладку и снимите флажок **Автонастройка представления в зависимости от быстродействия клиента**. Затем установите флажок вложенных **включить расширенное визуальное представление клиента**. Теперь можно просмотреть анимацию при построении проекта в ваш экспериментальный экземпляр Visual Studio.  
  
     В этой процедуре мы можем отобразить стандартные анимации Visual Studio, представляющего построения проекта или решения.  
  
2.  Откройте файл TestStatusBarCommand.cs и замените метод MenuItemCallback следующим кодом:  
  
    ```csharp  
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
  
3.  Скомпилируйте код и начните отладку.  
  
4.  Откройте **средства** в экспериментальном экземпляре Visual Studio и нажмите кнопку меню **TestStatusBarCommand вызова**.  
  
     Когда появится окно сообщения, вы также увидите анимации в строке состояния справа. После закрытия окна сообщения, исчезает анимации.
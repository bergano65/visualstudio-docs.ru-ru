---
title: Расширение строки состояния | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1ac7289489e1b7f3f2a047a10b6ace42fc15d94
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978574"
---
# <a name="extending-the-status-bar"></a>Расширение строки состояния
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для отображения сведений в нижней части интегрированной среды разработки можно использовать строку состояния Visual Studio.  
  
 При расширении строке состояния, можно отобразить сведения и пользовательского интерфейса в четырех регионах: область обратной связи, индикатор хода выполнения, область анимации и область конструктора. Область обратной связи позволяет отображать текст и выделить отображаемого текста. Индикатор хода выполнения будет отображаться ход добавочные коротким циклом выполнения операции, такие как сохранение файла. Область анимации отображается анимированный значок постоянно зациклен для долго выполняющейся операции или операции неопределенном длины, такие как построение нескольких проектов в решении. И область конструктора отображает номер строки и столбца положения курсора.  
  
 В строке состояния можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> интерфейс (из <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> службы). Кроме того, любой объект, размещенные на рамку окна можно зарегистрировать как строка клиентский объект состояния, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> интерфейс. Каждый раз, когда окно активируется, Visual Studio запрашивает у объекта, находящегося в этом окне для `IVsStatusbarUser` интерфейс. Если найден, он вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метод на возвращенный интерфейс и объект можно обновить строки состояния из этого метода. Окна, документов, например, можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метода, чтобы обновить сведения в области конструктора, когда они станут active.  
  
 В следующих процедурах предполагается, что вы знаете, как создать проект VSIX и добавьте пользовательские команды. Сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Изменение строки состояния  
 Эта процедура показано, как задать и получить текст, отображения статического текста и выделите текст, отображаемый в области обратной связи в строке состояния.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Чтение и запись в строке состояния  
  
1.  Создайте проект VSIX с именем **TestStatusBarExtension** и добавьте команду меню с именем **TestStatusBarCommand**.  
  
2.  В TestStatusBarCommand.cs замените код метода обработчика команд (MenuItemCallback) следующее:  
  
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
  
4.  Откройте **средства** меню в экспериментальном экземпляре Visual Studio. Нажмите кнопку **вызова TestStatusBarCommand** кнопки.  
  
     Вы увидите, что текст в строке теперь операций чтения состояния **«Мы только что написанный в строке состояния.»** и, появится окно сообщения содержит тот же текст.  
  
#### <a name="updating-the-progress-bar"></a>Обновление индикатора хода выполнения  
  
1.  В этой процедуре будет показано, как инициализировать и обновлять индикатор хода выполнения.  
  
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
  
4.  Откройте **средства** меню в экспериментальном экземпляре Visual Studio. Нажмите кнопку **вызова TestStatusBarCommand** кнопки.  
  
     Вы увидите, что текст в строке теперь операций чтения состояния **«Запись индикатор выполнения».** Вы также увидите индикатор выполнения обновляется каждую секунду в течение 20 секунд. После этого будут удалены в строке состояния и индикатор хода выполнения.  
  
#### <a name="displaying-an-animation"></a>Отображение анимации  
  
1.  В строке состояния отображается цикла анимации, которая указывает либо долго выполняющейся операции (например, построение нескольких проектов в решении). Если вы не видите этой анимации, убедитесь, что у вас есть правильный **Сервис / Параметры** параметры:  
  
     Перейдите к **Сервис/Параметры / Общие** вкладку и снимите флажок **Автонастройка представления в зависимости от быстродействия клиента**. Затем проверьте подпараметров **включить расширенное визуальное представление клиента**. Теперь можно просмотреть анимацию при сборке проекта в вашем экспериментальном экземпляре Visual Studio.  
  
     В этой процедуре мы отображаем стандартный анимации Visual Studio, которая представляет построение проекта или решения.  
  
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
  
4.  Откройте **средства** меню в экспериментальном экземпляре Visual Studio и нажмите кнопку **вызвать TestStatusBarCommand**.  
  
     Когда появится окно сообщения, вы увидите также анимации в строке состояния в правом углу. После закрытия окна сообщения, исчезает анимации.

---
title: "Создание расширения с помощью VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Создание расширения с помощью VSPackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как создать проект VSIX и добавить элемент проекта VSPackage. Мы используем VSPackage для получения службы Shell пользовательского интерфейса, чтобы отобразить окно сообщения.  
  
## Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Для получения дополнительной информации см. [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Создание VSPackage  
  
1.  Создайте проект VSIX с именем **FirstPackage**. Можно найти шаблон проекта VSIX в **Новый проект** диалоговом окне под **Visual C\# и расширяемость**.  
  
2.  При открытии проекта, добавление шаблона элемента пакета Visual Studio с именем **FirstPackage**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **Добавить или создать элемент**. В **Добавление нового элемента** диалоговое окно, последовательно выберите пункты **Visual C\# и расширяемость** и выберите **пакет Visual Studio**. В **имя** в нижней части окна, измените имя файла команд для **FirstPackage.cs**.  
  
3.  Выполните сборку решения и запустите отладку.  
  
     Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения о экспериментальный экземпляр в разделе [Экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
4.  В экспериментальном экземпляре откройте **средства\-расширения и обновления** окна. Вы должны увидеть **FirstPackage** здесь расширения. \(Если вы откроете **расширения и обновления** в работе экземпляра Visual Studio, вы не увидите **FirstPackage**\).  
  
## Загрузки VSPackage  
 На этом этапе модуль не загружается, поскольку нет ничего, который используется для загрузки. Обычно можно загрузить расширение при взаимодействии с его пользовательским Интерфейсом \(выбора команды в меню, открыв окно инструментов\) или путем указания, что VSPackage должны загружаться в определенном контексте пользовательского интерфейса. Дополнительные сведения о загрузке контекстов VSPackages и пользовательского интерфейса в разделе [Загрузка пакетов VSPackages](../extensibility/loading-vspackages.md). В этой процедуре мы покажем, как загрузить VSPackage при открытом решении.  
  
1.  Откройте файл FirstPackage.cs. Найдите объявление класса FirstPackage. Замените существующие атрибуты следующее:  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Давайте добавим сообщение, которое позволит нам загрузку VSPackage. Мы используем метод Initialize\(\) VSPackage это сделать, поскольку службы Visual Studio можно получить только после размещения VSPackage. \(Дополнительные сведения о получении служб см. в разделе [Практическое руководство: Получение службы](../Topic/How%20to:%20Get%20a%20Service.md).\) Замените код, который возвращает метод Initialize\(\) FirstPackage <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> службы возвращает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс и вызывает его <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> метод.  
  
    ```c#  
    protected override void Initialize()  
    {  
        base.Initialize();  
  
        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "FirstPackage",  
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result));  
    }  
    ```  
  
3.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
4.  Откройте решение в экспериментальном экземпляре. Появится окно сообщения, которое говорит **первый пакет внутри Initialize\(\)**.
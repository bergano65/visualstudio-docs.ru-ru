---
title: "Создание расширения с помощью пакетов VSPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb4ed4767146a07db6a4567768ee9a49fec97667
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-extension-with-a-vspackage"></a>Создание расширения с помощью пакетов VSPackage
В этом пошаговом руководстве показано, как создать проект VSIX и добавить элемент проекта VSPackage. Мы будем использовать VSPackage для получения службы пользовательского интерфейса, чтобы вывести на экран окно сообщения.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Создание пакета VSPackage  
  
1.  Создайте проект VSIX с именем **FirstPackage**. Шаблон проекта VSIX в можно найти **новый проект** диалогового окна в разделе **Visual C# / Extensibility**.  
  
2.  При открытии проекта, добавьте элемент шаблона пакета Visual Studio с именем **FirstPackage**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите на **Visual C# / Extensibility** и выберите **пакета Visual Studio**. В **имя** в нижней части окна, измените имя файла команд для **FirstPackage.cs**.  
  
3.  Выполните сборку решения и запустите отладку.  
  
     Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения о экспериментальный экземпляр, в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
4.  В экспериментальном экземпляре откройте **средства / расширения и обновления** окна. Вы увидите **FirstPackage** здесь расширения. (Если вы откроете **расширения и обновления** в работе экземпляра Visual Studio, вы не увидите **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>Загрузка VSPackage  
 На этом этапе модуль не загружается, поскольку нет ничего, который используется для загрузки. Как правило, можно загрузить расширение при взаимодействии с его пользовательским Интерфейсом (выбора команды в меню, открыв окно инструментов) или путем указания, что пакет VSPackage должен загружать в определенном контексте пользовательского интерфейса. Дополнительные сведения о загрузке контекстов пакеты VSPackage и пользовательского интерфейса см. в разделе [загрузке пакетов VSPackage](../extensibility/loading-vspackages.md). В этой процедуре мы покажем, как загрузить пакет VSPackage при открытом решении.  
  
1.  Откройте файл FirstPackage.cs. Найдите объявление класса FirstPackage. Замените существующие атрибуты следующее:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Давайте добавим сообщение, которое позволит нам загруженный пакет VSPackage. Мы используем метод Initialize() VSPackage для этого, так как службы Visual Studio можно получить только после размещения пакета VSPackage. (Дополнительные сведения о получении служб см. в разделе [как: доступ к службе](../extensibility/how-to-get-a-service.md).) Замените код, который возвращает метод Initialize() FirstPackage <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> службы возвращает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс и вызывает его <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> метод.  
  
    ```csharp  
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
  
4.  Откройте решение в экспериментальном экземпляре. Появится окно сообщения об ошибке **первого пакета внутри Initialize()**.
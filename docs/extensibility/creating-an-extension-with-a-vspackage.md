---
title: Создание расширения с помощью VSPackage | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50af15e1c15b5d0b6318c498923229778e8c0169
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500778"
---
# <a name="create-an-extension-with-a-vspackage"></a>Создание расширения с помощью VSPackage
В этом пошаговом руководстве показано, как создать проект VSIX и добавить элемент проекта VSPackage. Мы будем использовать пакет VSPackage, чтобы получить службу пользовательского интерфейса оболочки для отображения окна сообщения.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-vspackage"></a>Создание пакета VSPackage  
  
1.  Создайте проект VSIX с именем **FirstPackage**. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, в разделе **Visual C#** > **расширяемости**.  
  
2.  При открытии проекта, добавьте элемент шаблона пакета Visual Studio с именем **FirstPackage**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить** > **новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C#** > **расширяемости** и выберите **пакета Visual Studio**. В **имя** в нижней части окна, измените имя командного файла для *FirstPackage.cs*.  
  
3.  Выполните сборку решения и запустите отладку.  
  
     Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения о экспериментальный экземпляр, см. в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
4.  В экспериментальном экземпляре откройте **средства** > **расширения и обновления** окна. Вы должны увидеть **FirstPackage** здесь расширения. (Если вы откроете **расширения и обновления** в свой рабочий экземпляр Visual Studio, вы не увидите **FirstPackage**).  
  
## <a name="load-the-vspackage"></a>Загрузку пакета VSPackage  
 На этом этапе модуль не загружается, поскольку нет ничего, который используется для загрузки. Как правило, можно загрузить расширение при взаимодействии с его пользовательским Интерфейсом (нажав кнопку команды меню, открытие окна инструментов), либо указать, что VSPackage следует загрузить в определенном контексте пользовательского интерфейса. Дополнительные сведения о загрузке контексты пакетов VSPackage и пользовательского интерфейса, см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md). Для выполнения этой процедуры мы покажем, как загрузить пакет VSPackage, при открытом решении.  
  
1.  Откройте *FirstPackage.cs* файла. Найдите объявление `FirstPackage` класса. Замените существующие атрибуты следующее:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackage.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Давайте добавим сообщение, которое позволит нам загрузку VSPackage. Мы используем в пакете VSPackage `Initialize()` метод, чтобы сделать это, так как вы можете получить Visual Studio служб только в том случае, после размещения VSPackage. (Дополнительные сведения о получении службы см. в разделе [как: доступ к службе](../extensibility/how-to-get-a-service.md).) Замените `Initialize()` метод `FirstPackage` с кодом, который получает <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> служба, которую получает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс и вызывает его <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> метод.  
  
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
  
4.  Откройте решение в экспериментальном экземпляре. Вы должны увидеть окно сообщения с текстом **первого пакета внутри Initialize()**.
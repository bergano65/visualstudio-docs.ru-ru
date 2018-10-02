---
title: Создание расширения с помощью VSPackage | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea5e5320f612a1086e7bba2f63539470773078bf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572335"
---
# <a name="creating-an-extension-with-a-vspackage"></a>Создание расширения с помощью VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [создания расширения с помощью VSPackage](https://docs.microsoft.com/visualstudio/extensibility/creating-an-extension-with-a-vspackage).  
  
В этом пошаговом руководстве показано, как создать проект VSIX и добавить элемент проекта VSPackage. Мы будем использовать пакет VSPackage, чтобы получить службу пользовательского интерфейса оболочки для отображения окна сообщения.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Создание пакета VSPackage  
  
1.  Создайте проект VSIX с именем **FirstPackage**. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, в разделе **Visual C# / Extensibility**.  
  
2.  При открытии проекта, добавьте элемент шаблона пакета Visual Studio с именем **FirstPackage**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C# / Extensibility** и выберите **пакета Visual Studio**. В **имя** в нижней части окна, измените имя командного файла для **FirstPackage.cs**.  
  
3.  Выполните сборку решения и запустите отладку.  
  
     Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения о экспериментальный экземпляр, см. в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
4.  В экспериментальном экземпляре откройте **средства / расширения и обновления** окна. Вы должны увидеть **FirstPackage** здесь расширения. (Если вы откроете **расширения и обновления** в свой рабочий экземпляр Visual Studio, вы не увидите **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>Загрузка VSPackage  
 На этом этапе модуль не загружается, поскольку нет ничего, который используется для загрузки. Как правило, можно загрузить расширение при взаимодействии с его пользовательским Интерфейсом (нажав кнопку команды меню, открытие окна инструментов), либо указать, что VSPackage следует загрузить в определенном контексте пользовательского интерфейса. Дополнительные сведения о загрузке контексты пакетов VSPackage и пользовательского интерфейса, см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md). Для выполнения этой процедуры мы покажем, как загрузить пакет VSPackage, при открытом решении.  
  
1.  Откройте файл FirstPackage.cs. Найдите объявление класса FirstPackage. Замените существующие атрибуты следующее:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Давайте добавим сообщение, которое позволит нам загрузку VSPackage. Мы используем метод Initialize() VSPackage для этого, так как службы Visual Studio можно получить только после размещения VSPackage. (Дополнительные сведения о получении службы см. в разделе [как: доступ к службе](../extensibility/how-to-get-a-service.md).) Замените код, который возвращает метод Initialize() FirstPackage <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> служба, которую получает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс и вызывает его <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> метод.  
  
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


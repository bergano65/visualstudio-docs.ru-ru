---
title: Создание расширения с помощью VSPackage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ddad7149db75aa662f9427a301c04eaf925146f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197422"
---
# <a name="creating-an-extension-with-a-vspackage"></a>Создание расширения с помощью VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как создать проект VSIX и добавить элемент проекта VSPackage. Мы будем использовать VSPackage для получения службы оболочки пользовательского интерфейса, чтобы отобразить окно сообщения.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Создание VSPackage  
  
1. Создайте проект VSIX с именем **фирстпаккаже**. Шаблон проекта VSIX можно найти в диалоговом окне **Новый проект** в разделе **Visual C#/Extensibility (расширяемость**).  
  
2. Когда откроется проект, добавьте шаблон элемента пакета Visual Studio с именем **фирстпаккаже**. В **Обозреватель решений**щелкните правой кнопкой мыши узел проекта и выберите **Добавить/новый элемент**. В диалоговом окне **Добавление нового элемента** перейдите в раздел **Visual C#/Extensibility** и выберите **пакет Visual Studio**. В поле **имя** в нижней части окна измените имя файла команд на **FirstPackage.CS**.  
  
3. Выполните сборку решения и запустите отладку.  
  
     Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения об экспериментальном экземпляре см. [в статье экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
4. В экспериментальном экземпляре откройте окно **Сервис/расширения и обновления** . Здесь вы увидите расширение **фирстпаккаже** . (Если вы открыли **расширения и обновления** в рабочем экземпляре Visual Studio, вы не увидите **фирстпаккаже**).  
  
## <a name="loading-the-vspackage"></a>Загрузка VSPackage  
 На этом этапе расширение не загружается, так как нет ничего, что приводит к его загрузке. Обычно расширение можно загрузить при взаимодействии с его ИНТЕРФЕЙСом (щелкнув команду меню, открыв окно инструментов) или указав, что пакет VSPackage должен загружаться в определенном контексте пользовательского интерфейса. Дополнительные сведения о загрузке пакетов VSPackage и контекстов пользовательского интерфейса см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md). В этой процедуре мы покажем, как загрузить VSPackage, когда решение открыто.  
  
1. Откройте файл FirstPackage.cs. Найдите объявление класса Фирстпаккаже. Замените существующие атрибуты следующим:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2. Добавим сообщение, которое поможет нам убедиться, что пакет VSPackage загружен. Для этого мы используем метод Initialize () VSPackage, так как вы можете получить доступ к службам Visual Studio только после того, как пакет VSPackage установлен на сайте. (Дополнительные сведения о получении служб см. [в разделе как получить службу](../extensibility/how-to-get-a-service.md).) Замените метод Initialize () объекта Фирстпаккаже кодом, который получает <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> службу, возвращает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс и вызывает его <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> метод.  
  
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
  
3. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
4. Откройте решение в экспериментальном экземпляре. Должно отобразиться окно сообщения, **в котором сначала указывается пакет в разделе Initialize ()**.

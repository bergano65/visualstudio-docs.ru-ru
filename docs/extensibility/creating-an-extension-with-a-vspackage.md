---
title: Создание расширения с VSPackage (ru) Документы Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1037ebcc58cc4183e6f02119bc7b46abfc132f52
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739535"
---
# <a name="create-an-extension-with-a-vspackage"></a>Создать расширение с VSPackage

В этом пошаговом показании показано, как создать проект VSIX и добавить элемент проекта VSPackage. Мы будем использовать VSPackage, чтобы получить службу UI Shell для того, чтобы показать окно сообщений.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-vspackage"></a>Создание VSPackage

1. Создайте проект VSIX под названием **FirstPackage**. Шаблон проекта VSIX можно найти в диалоге **нового проекта,** ища "vsix".

2. Когда проект откроется, добавьте шаблон элемента пакета Visual Studio под названием **FirstPackage.** В **Solution Explorer**, правой кнопкой мыши узла проекта и выберите **Добавить** > **новый пункт**. В диалоге **Добавить новый элемент,** перейдите на **Visual C е** > **Расширяемость** и выберите **Пакет Visual Studio.** В поле **«Имя»** в нижней части окна измените имя файла команды на *FirstPackage.cs.*

3. Выполните сборку решения и запустите отладку.

    Появляется экспериментальный экземпляр Visual Studio. Для получения дополнительной информации об экспериментальном экземпляре [см.](../extensibility/the-experimental-instance.md)

4. В экспериментальном примере откройте окно расширения и обновления **инструментов.** > **Extensions and Updates** Вы должны увидеть расширение **FirstPackage** здесь. (Если вы **откроете расширения и обновления** в рабочем экземпляре Visual Studio, вы не **увидите FirstPackage).**

## <a name="load-the-vspackage"></a>Загрузите VSPackage

На данный момент расширение не загружается, потому что нет ничего, что заставляет его загружаться. Как правило, можно загрузить расширение при взаимодействии с uI (нажатие команды меню, открытие окна инструмента) или указание мецената, который должен загрузить VSPackage в определенном контексте uI. Для получения дополнительной информации о загрузке VSPackages и контекстов uI [см.](../extensibility/loading-vspackages.md) Для этой процедуры мы покажем вам, как загрузить VSPackage, когда решение открыто.

1. Откройте *файл FirstPackage.cs.* Ищите декларацию `FirstPackage` класса. Замените существующие атрибуты следующими атрибутами:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Давайте добавим сообщение, которое позволяет нам знать, что VSPackage загрузился. Мы используем `Initialize()` метод VSPackage для этого, потому что вы можете получить услуги Visual Studio только после того, как VSPackage был расположен. (Для получения дополнительной информации о получении услуг, [см. Как: Получить услугу](../extensibility/how-to-get-a-service.md).) Замените `Initialize()` метод `FirstPackage` с кодом, который <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> получает службу, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> получает интерфейс и вызывает его метод.

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

3. Выполните сборку решения и запустите отладку. Появляется экспериментальный экземпляр.

4. Откройте решение в экспериментальном экземпляре. Вы должны увидеть окно сообщения, которое говорит **Первый пакет внутри инициализации()**.

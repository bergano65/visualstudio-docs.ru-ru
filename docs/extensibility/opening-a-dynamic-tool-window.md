---
title: Открытие окна динамического инструмента (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff971f980b0a9b2fb0e22f56fb0ace752829c2c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702263"
---
# <a name="open-a-dynamic-tool-window"></a>Открыть динамическое окно инструмента
Окна инструментов обычно открываются из команды в меню или эквивалентного ярлыка клавиатуры. Однако иногда может потребоваться окно инструментов, которое открывается всякий раз, когда применяется определенный контекст uI, и закрывается, когда контекст uI больше не применяется. Эти типы окон инструмента называются *динамическими* или *автоматически видимыми.*

> [!NOTE]
> Список предопределенных контекстов uI <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>см.

 Если вы хотите открыть динамическое окно инструмента при запуске, и возможно, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> что создание сбой, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> вы должны реализовать интерфейс и проверить условия сбоя в методе. Для того, чтобы оболочка знала, что у вас есть динамическое окно `SupportsDynamicToolOwner` инструмента, которое должно быть открыто при запуске, необходимо добавить значение (установить до 1) к регистрации пакета. Это значение не является <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>частью стандарта, поэтому необходимо создать пользовательский атрибут, чтобы добавить его. Для получения дополнительной информации о пользовательских атрибутах [см.](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)

 Используйте <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> для открытия окна инструмента. Окно инструмента создается по мере необходимости.

> [!NOTE]
> Динамическое окно инструмента может быть закрыто пользователем. Если требуется создать команду меню, чтобы пользователь мог повторно открыть окно инструмента, команда меню должна быть включена в том же контексте пользовательского интерфейса, который открывает окно инструмента, и отключен в противном случае.

## <a name="to-open-a-dynamic-tool-window"></a>Открытие динамического окна инструмента

1. Создайте проект VSIX под названием **DynamicToolWindow** и добавьте шаблон элемента окна инструмента, названный *DynamicWindowPane.cs.* Для получения дополнительной информации [см. Создать расширение с окном инструмента](../extensibility/creating-an-extension-with-a-tool-window.md).

2. В *файле DynamicWindowPanePackage.cs* найти декларацию DynamicWindowPanePackage. Добавьте <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> и атрибуты для регистрации окна инструмента.

    ```vb
    [ProvideToolWindow(typeof(DynamicWindowPane)]
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]
    [Guid(DynamicWindowPanePackage.PackageGuidString)]
    public sealed class DynamicWindowPanePackage : Package
    {. . .}
    ```

     Атрибуты выше регистрируют окно инструмента под названием DynamicWindowPane как переходное окно, которое не сохраняется при закрытии и повторном открытии Visual Studio. DynamicWindowPane открывается <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> всякий раз, когда применяется, и закрывается в противном случае.

3. Выполните сборку решения и запустите отладку. Экспериментальный экземпляр должен появиться. Вы не должны видеть окно инструмента.

4. Откройте проект в экспериментальном примере. Должно появиться окно инструмента.

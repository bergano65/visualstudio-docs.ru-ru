---
title: Открытие динамического окна инструментов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09b81294abc708cf7616dad03b5dd7333d6a1719
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842968"
---
# <a name="opening-a-dynamic-tool-window"></a>Открытие динамического окна инструментов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Окна инструментов обычно открываются из команды меню или эквивалентного сочетания клавиш. Иногда может потребоваться окно инструментов, которое открывается каждый раз, когда применяется конкретный контекст пользовательского интерфейса, и закрывается, когда контекст пользовательского интерфейса больше не применяется. Такие окна инструментов называются *динамическими* или *видимыми*.  
  
> [!NOTE]
> Список предопределенных контекстов пользовательского интерфейса см. в разделе <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> . В качестве значения  
  
 Если необходимо открыть Динамическое окно инструментов при запуске, а создание завершится ошибкой, необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> интерфейс и проверить условия сбоя в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> методе. Чтобы оболочка знала о том, что имеется динамическое окно инструментов, которое должно быть открыто при запуске, необходимо добавить `SupportsDynamicToolOwner` значение (значение 1) в регистрацию пакета. Это значение не входит в стандарт <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> , поэтому необходимо создать настраиваемый атрибут, чтобы добавить его. Дополнительные сведения о настраиваемых атрибутах см. [в разделе Использование пользовательского атрибута регистрации для регистрации расширения](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 Используйте <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> для открытия окна инструментов. Окно инструментов создается по мере необходимости.  
  
> [!NOTE]
> Динамическое окно инструментов может быть закрыто пользователем. Если вы хотите создать команду меню, чтобы пользователь мог снова открыть окно инструментов, команда меню должна быть включена в том же контексте пользовательского интерфейса, который открывает окно инструментов, и в противном случае отключен.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Открытие динамического окна инструментов  
  
1. Создайте проект VSIX с именем **динамиктулвиндов** и добавьте шаблон элемента окна инструментов с именем **DynamicWindowPane.CS**. Дополнительные сведения см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2. В файле DynamicWindowPanePackage.cs найдите объявление Динамиквиндовпанепаккаже. Добавьте <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> атрибуты и т:Микрософт.висуалстудио.Шелл.провидетулвиндоввисибилитяттрибуте для регистрации окна инструментов.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     При этом окно инструментов с именем Динамиквиндовпане будет зарегистрировано как временное окно, которое не сохраняется при закрытии и повторном открытии Visual Studio. Динамиквиндовпане открывается каждый раз <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> , когда применяется, и закрывается в противном случае.  
  
3. Выполните сборку решения и запустите отладку. Должен отобразиться экспериментальный экземпляр. Окно инструментов не отображается.  
  
4. Откройте проект в экспериментальном экземпляре. Должно отобразиться окно инструментов.

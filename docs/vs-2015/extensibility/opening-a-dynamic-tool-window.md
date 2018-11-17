---
title: Открытие динамического окна инструментов | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 073e8a2e7ff13dad0e413aa47b7875260f612cd2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773799"
---
# <a name="opening-a-dynamic-tool-window"></a>Открытие динамического окна инструментов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Окна инструментов обычно открываются из команды в меню или соответствующих сочетаний клавиш. В некоторых случаях Однако может потребоваться окна инструментов, которое открывается при определенном контексте пользовательского интерфейса применяется и закрывается при контекст пользовательского интерфейса больше не применяется. Окна инструментов, как они называются *динамическое* или *автоматическим отображением*.  
  
> [!NOTE]
>  Список предварительно определенных контекстов пользовательского интерфейса, см. в разделе <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>. Для  
  
 Если вы хотите открыть динамического окна инструментов при запуске и существует возможность создания переход на другой, необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> интерфейс и проверить условия сбоя в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> метод. Чтобы оболочке известно о наличии динамического окна инструментов, должен быть открыт во время запуска, необходимо добавить `SupportsDynamicToolOwner` (задано значение 1) в пакет регистрации. Это значение не является частью стандарта <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, поэтому необходимо создать настраиваемый атрибут, чтобы добавить его. Дополнительные сведения о настраиваемых атрибутах см. в разделе [использование пользовательского атрибута регистрации для регистрации расширения](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 Используйте <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> для открытия окна инструментов. Окно инструментов создается при необходимости.  
  
> [!NOTE]
>  Пользователь может быть закрывает динамического окна инструментов. Если вы хотите создать команду меню, поэтому пользователь может снова откройте окно инструментов, в том же контексте пользовательского интерфейса, что окно инструментов, а в противном случае отключено должно быть включено команду меню.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Открытие динамического окна инструментов  
  
1.  Создайте проект VSIX с именем **DynamicToolWindow** и добавление шаблона элемента окна инструментов с именем **DynamicWindowPane.cs**. Дополнительные сведения см. в разделе [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  В файле DynamicWindowPanePackage.cs поиске DynamicWindowPanePackage объявления. Добавление <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> и T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute атрибуты для регистрации окна инструментов.  
  
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
  
     При этом регистрируется с именем DynamicWindowPane как временные окна, которое не сохраняется при закрытии и повторном открытии Visual Studio окно инструментов. Открывается DynamicWindowPane всякий раз, когда <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> применяется и закрыт, в противном случае.  
  
3.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр. Вы не увидите окна инструментов.  
  
4.  Откройте проект в экспериментальном экземпляре. Появится окно инструментов.


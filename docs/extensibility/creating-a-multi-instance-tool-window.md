---
title: Создание окна инструмента Multi-Instance (фото) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33585f623f846e16200d430ad2c886fe0874b537
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739622"
---
# <a name="create-a-multi-instance-tool-window"></a>Создание окна инструмента с несколькими экземплярами
Вы можете запрограммировать окно инструмента так, чтобы несколько экземпляров его можно было открыть одновременно. По умолчанию окна инструмента могут иметь только один экземпляр открытым.

При использовании окна инструмента мультиinstancea можно отобразить одновременно несколько связанных источников информации. Например, можно поместить многолинейный <xref:System.Windows.Forms.TextBox> элемент управления в окно инструмента нескольких экземпляров, чтобы несколько фрагментов кода были одновременно доступны во время сеанса программирования. Кроме того, например, <xref:System.Windows.Forms.DataGrid> можно поместить окно списка управления и выпадения в окно инструмента с несколькими экземплярами, чтобы одновременно отслеживать несколько источников данных в режиме реального времени.

## <a name="create-a-basic-single-instance-tool-window"></a>Создание базового (одноэкземплярного) окна инструмента

1. Создайте проект под названием **MultiInstanceToolWindow** с помощью шаблона VSIX и добавьте шаблон пользовательского окна инструмента под названием **MIToolWindow.**

    > [!NOTE]
    > Для получения дополнительной информации о создании расширения с окном инструмента [см. Создать расширение с окном инструмента.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="make-a-tool-window-multi-instance"></a>Сделать окно инструмента мультиэкземпляром

1. Откройте *файл MIToolWindowPackage.cs* `ProvideToolWindow` и найдите атрибут. и `MultiInstances=true` параметр, как показано в следующем примере:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. В *MIToolWindowCommand.cs* файле `ShowToolWindos()` найдите метод. В этом методе <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> вызовите `create` метод `false` и установите его флаг таким образом, чтобы `id` он итерироваться через существующие экземпляры окна инструмента до тех пор, пока не будет найден доступный.

3. Чтобы создать экземпляр окна инструмента, <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> позвоните `id` в метод и `create` установите его на доступное значение, а его флаг — на `true`.

    По умолчанию значение `id` параметра <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> метода. `0` Это значение создает окно инструмента одного экземпляра. Для более чем одного экземпляра, который будет `id`размещен, каждый экземпляр должен иметь свой собственный уникальный .

4. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> на объект, <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> который возвращается свойством экземпляра окна инструмента.

5. По умолчанию `ShowToolWindow` метод, создаваемый шаблоном элемента «окно инструмента», создает окно инструмента одного экземпляра. В следующем примере показано, как изменить `ShowToolWindow` метод для создания нескольких экземпляров.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```

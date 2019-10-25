---
title: Обновление пользовательского интерфейса | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf41a41e68aa73e07bdcafe8bcdcd335fff6e6eb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718786"
---
# <a name="updating-the-user-interface"></a>Обновление пользовательского интерфейса
После реализации команды можно добавить код для обновления пользовательского интерфейса с состоянием новых команд.

 В типичном приложении Win32 набор команд можно постоянно опрашивать, а состояние отдельных команд можно настроить по мере их просмотра пользователем. Тем не менее, поскольку оболочка [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] может размещать неограниченное количество пакетов VSPackage, расширенный опрос может снизить скорость реагирования, особенно опрос между сборками взаимодействия между управляемым кодом и COM.

### <a name="to-update-the-ui"></a>Обновление пользовательского интерфейса

1. Выполните одно из следующих действий.

    - Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.

         Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> можно получить из службы <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, как показано ниже.

        ```csharp
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)
        {
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));
            if (vsShell != null)
            {
                int hr = vsShell.UpdateCommandUI(0);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
            }
        }

        ```

         Если параметр <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> не равен нулю (`TRUE`), обновление выполняется синхронно и немедленно. Рекомендуется передать ноль (`FALSE`) для этого параметра, чтобы обеспечить хорошую производительность. Если вы хотите избежать кэширования, примените флаг `DontCache` при создании команды в файле. vsct. Тем не менее используйте флаг с осторожностью или производительность может снизиться. Дополнительные сведения о флагах команд см. в документации по [элементу флага команды](../extensibility/command-flag-element.md) .

    - В пакетах VSPackage, где размещается элемент управления ActiveX с помощью модели встроенной активации в окне, может быть удобнее использовать метод <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>. Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> в интерфейсе <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> и метод <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> в интерфейсе <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> функционально эквивалентны. Обе из них приводят к повторному запросу состояния всех команд в среде. Как правило, обновление выполняется не сразу. Вместо этого обновление откладывается до времени простоя. Оболочка кэширует состояние команды, чтобы обеспечить хорошую производительность. Если вы хотите избежать кэширования, примените флаг `DontCache` при создании команды в файле. vsct. Тем не менее, используйте флаг с осторожностью, так как производительность может снизиться.

         Обратите внимание, что можно получить интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>, вызвав метод `QueryInterface` для объекта <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> или путем получения интерфейса из службы <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>.

## <a name="see-also"></a>См. также
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Реализация](../extensibility/internals/command-implementation.md)
---
title: Обновление пользовательского интерфейса | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c51ae790eb35645fbe9aec5d9c422e1051aaa69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698889"
---
# <a name="updating-the-user-interface"></a>Обновление пользовательского интерфейса
После реализации команды можно добавить код для обновления пользовательского интерфейса с состоянием новых команд.

 В типичном приложении Win32 набор команд можно постоянно опрашивать, а состояние отдельных команд можно настроить по мере их просмотра пользователем. Однако, поскольку [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] оболочка может размещать неограниченное количество пакетов VSPackage, обширный опрос может снизить скорость реагирования, особенно опрос между сборками взаимодействия между управляемым кодом и com.

### <a name="to-update-the-ui"></a>Обновление пользовательского интерфейса

1. Выполните одно из следующих действий.

    - Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> .

         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>Интерфейс можно получить из <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> службы следующим образом.

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

         Если значение параметра не равно <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> нулю ( `TRUE` ), обновление выполняется синхронно и немедленно. Рекомендуется передать ноль ( `FALSE` ) для этого параметра, чтобы обеспечить хорошую производительность. Если вы хотите избежать кэширования, примените этот `DontCache` флаг при создании команды в файле. vsct. Тем не менее используйте флаг с осторожностью или производительность может снизиться. Дополнительные сведения о флагах команд см. в документации по [элементу флага команды](../extensibility/command-flag-element.md) .

    - В пакетах VSPackage, в которых размещается элемент управления ActiveX с помощью модели активации на месте в окне, может оказаться удобнее использовать <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> метод. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>Метод в <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейсе и <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> метод в <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> интерфейсе функционально эквивалентны. Обе из них приводят к повторному запросу состояния всех команд в среде. Как правило, обновление выполняется не сразу. Вместо этого обновление откладывается до времени простоя. Оболочка кэширует состояние команды, чтобы обеспечить хорошую производительность. Если вы хотите избежать кэширования, примените этот `DontCache` флаг при создании команды в файле. vsct. Тем не менее, используйте флаг с осторожностью, так как производительность может снизиться.

         Обратите внимание, что интерфейс можно получить <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> , вызвав `QueryInterface` метод для <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> объекта или получив интерфейс от <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> службы.

## <a name="see-also"></a>См. также раздел
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Реализация](../extensibility/internals/command-implementation.md)

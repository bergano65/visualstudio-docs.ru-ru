---
title: Обновление пользовательского интерфейса (ru) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698889"
---
# <a name="updating-the-user-interface"></a>Обновление пользовательского интерфейса
После реализации команды можно добавить код для обновления пользовательского интерфейса в состоянии новых команд.

 В типичном приложении Win32 набор команд может быть постоянно опрошен, а состояние отдельных команд может быть скорректировано по мере их просмотра пользователем. Однако, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] поскольку оболочка может принимать неограниченное количество VSPackages, обширный опрос может уменьшить отзывчивость, особенно опросы между межопомнейными сборками между управляемым кодом и COM.

### <a name="to-update-the-ui"></a>Обновление uI

1. Выполните одно из следующих действий.

    - Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> .

         Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> можно получить из <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> службы, следующим образом.

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

         Если параметр <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> ненулевой (),`TRUE`то обновление выполняется синхронно и сразу. Мы рекомендуем вам пройти`FALSE`ноль () для этого параметра, чтобы помочь сохранить хорошую производительность. Если вы хотите избежать кэширования, нанесите `DontCache` флаг при создании команды в файле .vsct. Тем не менее, использовать флаг осторожно или производительность может снизиться. Для получения дополнительной информации о флагах команд смотрите документацию [элемента флага команд.](../extensibility/command-flag-element.md)

    - В VSPackages, которые размещают элемент управления ActiveX, используя модель активации в <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> окне, может быть удобнее использовать метод. Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> в <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейсе <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> и метод <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> в интерфейсе функционально эквивалентны. И то, и другое приводит к повторному запросу состояния всех команд. Как правило, обновление выполняется не сразу. Вместо этого обновление откладывается до простоя. Оболочка кэшает состояние команды, чтобы помочь поддерживать хорошую производительность. Если вы хотите избежать кэширования, нанесите `DontCache` флаг при создании команды в файле .vsct. Тем не менее, используйте флаг осторожно, так как производительность может снизиться.

         Обратите внимание, что <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> вы можете `QueryInterface` получить <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> интерфейс, позвонив по <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> методу на объект или получив интерфейс от службы.

## <a name="see-also"></a>См. также
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Реализация](../extensibility/internals/command-implementation.md)

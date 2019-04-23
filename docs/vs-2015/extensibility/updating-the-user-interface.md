---
title: Обновление пользовательского интерфейса | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db5be965119d1564f2a4bf8a15892af7142663e0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046803"
---
# <a name="updating-the-user-interface"></a>Обновление пользовательского интерфейса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

После выполнения команды, можно добавить код для обновления пользовательского интерфейса с состоянием новых команд.  
  
 В типичном приложении Win32 при этом набор команд можно постоянно опрашивать и состояние отдельных команд может быть скорректирован пользователь просматривает их. Тем не менее поскольку [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] оболочки можно размещать неограниченное число пакетов VSPackage, обширные опроса может уменьшить время отклика, особенно опроса через сборки взаимодействия между управляемым кодом и COM.  
  
### <a name="to-update-the-ui"></a>Обновление пользовательского интерфейса  
  
1. Выполните одно из следующих действий.  
  
    - Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Интерфейса можно получить из <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> службы, следующим образом.  
  
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
  
         Если параметр <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> имеет ненулевое значение (`TRUE`), то обновление выполняется синхронно и немедленно. Мы рекомендуем передавать ноль (`FALSE`) для этого параметра, чтобы помочь поддерживать высокую производительность. Если вы хотите избежать кэширования, примените `DontCache` флаг при создании команды в vsct-файле. Тем не менее, используйте флаг осторожно, или может привести к снижению производительности. Дополнительные сведения о флаги команды, см. в разделе [элемент Commandflag](../extensibility/command-flag-element.md) документации.  
  
    - В пакеты VSPackage, в котором размещен элемент управления ActiveX с помощью модели встроенной активации в окне, возможно, удобнее использовать <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> метод. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> Метод в <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс и <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> метод в <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> интерфейс функционально эквивалентны. Оба метода приводят среды, чтобы повторно запросить состояние всех команд. Как правило обновление не выполняется немедленно. Вместо этого обновление откладывается до времени простоя. Оболочка кэширует состояния команд, чтобы помочь поддерживать высокую производительность. Если вы хотите избежать кэширования, примените `DontCache` флаг при создании команды в vsct-файле. Тем не менее осторожно используйте флаг может привести к снижению производительности.  
  
         Обратите внимание, что вы можете получить <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> интерфейс путем вызова `QueryInterface` метод <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> объекта или по получение интерфейса из <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> службы.  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Реализация](../extensibility/internals/command-implementation.md)

---
title: "Обновление пользовательского интерфейса | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "интерфейсы пользователя, обновление"
  - "команды, обновление пользовательского интерфейса"
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 41
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 41
---
# Обновление пользовательского интерфейса
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

После выполнения команды можно добавить код для обновления пользовательского интерфейса с состоянием новой команды.  
  
 В типичном приложении Win32 постоянно опрашивать набор команд и состояния отдельных команд может быть скорректирован пользователь просматривает их. Однако поскольку [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] оболочки можно разместить неограниченное количество VSPackages, обширные опроса может уменьшить время отклика, особенно опроса между сборками взаимодействия между управляемым кодом и COM.  
  
### Для обновления пользовательского интерфейса  
  
1.  Выполните одно из следующих действий.  
  
    -   Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Интерфейс может быть получен из <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> службы, как показано ниже.  
  
        ```c#  
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
  
         Если параметр <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> не равно нулю \(`TRUE`\), то обновление выполняется синхронно и немедленно. Мы рекомендуем передавать ноль \(`FALSE`\) для этого параметра поддерживать высокую производительность. Если требуется избежать кэширования, применить `DontCache` флаг при создании команды в файл .vsct. Тем не менее, используйте флаг осторожно или может привести к снижению производительности. Дополнительные сведения о флагах командной см [Элемент Command флаг](../extensibility/command-flag-element.md) документации.  
  
    -   В пакеты VSPackage, размещение элемента управления ActiveX с помощью модели активации на месте в окне, возможно, удобнее всего использовать <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> метода.<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс и <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> метод <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> Интерфейс функционально эквивалентны. Оба метода приводят в среде для повторного запроса состояния всех команд. Как правило обновление не выполняется немедленно. Вместо этого обновления откладывается до времени простоя. Оболочка кэширует состояние команды в целях обеспечения высокой производительности. Если требуется избежать кэширования, применить `DontCache` флаг при создании команды в файл .vsct. Тем не менее осторожно используйте флаг потому, что может привести к снижению производительности.  
  
         Обратите внимание, что можно получить <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> интерфейс путем вызова `QueryInterface` метод <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> объекта или при получении интерфейс из <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> службы.  
  
## См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Реализация](../extensibility/internals/command-implementation.md)
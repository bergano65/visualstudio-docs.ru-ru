---
title: "Обновление пользовательского интерфейса | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: "41"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02bf66cba145b1d5fdaea899ca3af4ca2bcefbe1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="updating-the-user-interface"></a>Обновление пользовательского интерфейса
После выполнения команды можно добавить код для обновления пользовательского интерфейса с состоянием новой команды.  
  
 В типичном приложении Win32 постоянно опрашивать набор команд и состояние отдельных команд может настраиваться при их просмотре пользователем. Тем не менее поскольку [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] оболочка может содержать неограниченное количество пакетов VSPackage, широко опроса может уменьшить время отклика, особенно опроса через сборки взаимодействия между управляемым кодом и COM.  
  
### <a name="to-update-the-ui"></a>Обновление пользовательского интерфейса  
  
1.  Выполните одно из следующих действий.  
  
    -   Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Интерфейса могут быть получены из <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> службы, как показано ниже.  
  
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
  
         Если параметр <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> не равно нулю (`TRUE`), то обновление выполняется синхронно, так и немедленно. Мы рекомендуем передавать ноль (`FALSE`) для этого параметра в целях обеспечения оптимальной производительности. Если вы хотите избежать кэширования, примените `DontCache` флаг при создании команды в vsct-файле. Тем не менее, использовать флаг с осторожностью, или может снизиться производительность. Дополнительные сведения о флагах командной см. в разделе [элемент Command флаг](../extensibility/command-flag-element.md) документации.  
  
    -   В пакеты VSPackage, где размещен элемент управления ActiveX, с помощью модели встроенной активации в окне, может быть более удобным использовать <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> метода. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> Метод в <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс и <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> метод в <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> интерфейс функционально эквивалентны. Оба метода приводят среды для выполнения повторного запроса состояния всех команд. Как правило обновление не выполняется немедленно. Вместо этого обновления откладывается до времени простоя. Оболочка кэширует состояния команды в целях обеспечения оптимальной производительности. Если вы хотите избежать кэширования, примените `DontCache` флаг при создании команды в vsct-файле. Тем не менее осторожно используйте флаг может привести к снижению производительности.  
  
         Обратите внимание, что вы можете получить <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> интерфейса путем вызова `QueryInterface` метод <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> объекта или путем получения интерфейса из <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> службы.  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Реализация](../extensibility/internals/command-implementation.md)
---
title: "Объект VSCodeWindow | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2de0998a3d89c1af3e18fa60aa3f8511716f6165
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="vscodewindow-object"></a>Объект VSCodeWindow
Окно кода является специализированные документа, можно включить одно или несколько представлений текста обычно <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекта.  
  
 С точки зрения архитектуры окно кода является окно документа, в котором находится внутри рамки окна. С функциональной области окна кода — просто это окно документов с дополнительными возможностями. В режиме многодокументного интерфейса (MDI) окно кода — дочерняя рамка MDI. Дополнительные сведения см. в разделе [Настройка окна кода с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 В следующей таблице приведены интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> объекта.  
  
|Метод|Описание:|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Предоставляет общий доступ к механизм для поиска службы, определяющий глобальный уникальный идентификатор (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Представляет несколько дочерних интерфейса (MDI) документа, содержащий одно или несколько представлений кода.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Заполняет рамку окна.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Изменение фигур](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
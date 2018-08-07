---
title: Объект VSCodeWindow | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9ef7d4b190a9b2c1a487fb70df33726ca9b3ed4
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586278"
---
# <a name="vscodewindow-object"></a>Объект VSCodeWindow
Окно кода — это окно специализированные документов, который может включать одно или несколько представлений текста, обычно <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекта.  
  
 С точки зрения архитектуры окно кода — это окно документов, который находится в пределах фрейма окна. С функциональной точки зрения окно кода — просто это окно документов с помощью дополнительных функций. В режиме многодокументного интерфейса (MDI) в окне кода является дочерняя рамка MDI. Дополнительные сведения см. в разделе [Настройка кода windows, используя старый API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 В следующей таблице приведены интерфейсы <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> объекта.  
  
|Метод|Описание:|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Предоставляет универсальный доступ механизм для поиска службы, определяющий глобальный уникальный идентификатор (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Представляет несколько дочерних интерфейса (MDI) документа, содержащий одно или несколько представлений кода.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Заполняет рамку окна.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Изменение фигур](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
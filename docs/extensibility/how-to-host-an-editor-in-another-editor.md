---
title: "Как: размещения в другом редакторе редактор | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 26819cccc4f5359da83684575423f8d0be276497
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Как: размещения редактор в другом редакторе
В Visual Studio можно размещать одного редактора в другую, указав в качестве родительского окна главного окна. Чтобы сделать это, задайте параметры <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> и <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> на дочерние окна.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Настройка окна для размещения редактор  
  
1.  Назначьте редактор размещенный редактор путем создания дочерней области окна.  
  
     Эта панель доступна, куда текстового редактора.  
  
2.  Создание размещения с помощью редактора <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> метод.  
  
3.  Задать <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> и <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> свойства в реализации фрейм окна размещенный редактор, передав в качестве параметров для этих свойств <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> метода, соответственно.  
  
     Если вам нужно получить эти параметры, передайте эти свойства, чтобы <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод.  
  
4.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод для автономной редактора.  
  
     В области размещенного содержащего редактора откроется редактор.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 **Конструктор приложений** в Visual Studio Team Edition для архитекторов приведен пример размещения в другом редакторе фрейм окна редактора. **Конструктор приложений** содержит других конструкторов в правой области. Панели конструктора (или **свойства** страницы) для каждого из автономной конструкторы, добавленного к содержащей рамки окна.
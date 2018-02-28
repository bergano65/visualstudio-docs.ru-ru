---
title: "Как: размещения в другом редакторе редактор | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 685ad1d619fdf9f04fe1a9cd1122a9e6ed3ba025
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
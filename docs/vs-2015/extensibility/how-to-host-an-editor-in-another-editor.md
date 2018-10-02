---
title: 'Практическое: размещения в другом редакторе редактор | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6390f5550c445239fbd8f8f72f9c8c4ad013665a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560685"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Практическое: размещения редактор в другом редакторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: редактор узлов в другом редакторе](https://docs.microsoft.com/visualstudio/extensibility/how-to-host-an-editor-in-another-editor).  
  
В Visual Studio можно разместить один редактор внутри другого, указав в качестве родительского окна главного окна. Чтобы сделать это, установите параметры <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> и <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> на родительского окна области.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Чтобы настроить фрейм окна для размещения редактора  
  
1.  Назначьте редактор размещенного редактора, создав область дочернего окна.  
  
     Эта панель доступна, куда текстового редактора.  
  
2.  Создание редакторе размещения с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> метод.  
  
3.  Задайте <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> и <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> свойства в реализации фрейма окна размещенного редактора, передав в качестве параметров для этих свойств <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> метода, соответственно.  
  
     Если вам нужно получить эти параметры, передать эти свойства, чтобы <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод.  
  
4.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод для автономной редактора.  
  
     В области размещенной содержащего редактора откроется редактор.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 **Конструктор приложений** в Visual Studio Team Edition для архитекторов является примером фрейм окна редактора, размещения в другом редакторе. **Конструктор приложений** размещает другие конструкторы в его панели справа. Панели конструктора (или **свойства** страницы) для каждого из автономной конструкторы, добавленного на рамку окна, содержащего.


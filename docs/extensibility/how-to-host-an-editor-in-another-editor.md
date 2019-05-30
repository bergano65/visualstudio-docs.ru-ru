---
title: Практическое руководство. Размещение в другом редакторе редактор | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1ef547c5584cba256a8f28bf2b0ba1de2ac7448
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351967"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Практическое руководство. Узел редактор в другом редакторе

В Visual Studio можно разместить один редактор внутри другого, указав в качестве родительского окна главного окна. Чтобы сделать это, установите параметры <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> и <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> на родительского окна области.

## <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Чтобы настроить фрейм окна для размещения редактора

1. Назначьте редактор размещенного редактора, создав область дочернего окна.

     Эта панель доступна, куда текстового редактора.

2. Создание редакторе размещения с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> метод.

3. Задайте <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> и <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> свойства в реализации фрейма окна размещенного редактора, передав в качестве параметров для этих свойств <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> метода, соответственно.

     Если вам нужно получить эти параметры, передать эти свойства, чтобы <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод.

4. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод для автономной редактора.

     В области размещенной содержащего редактора откроется редактор.

## <a name="robust-programming"></a>Отказоустойчивость

**Конструктор приложений** в Visual Studio Team Edition для архитекторов является примером фрейм окна редактора, размещения в другом редакторе. **Конструктор приложений** размещает другие конструкторы в его панели справа. Панели конструктора (или **свойства** страницы) для каждого из автономной конструкторы, добавленного на рамку окна, содержащего.
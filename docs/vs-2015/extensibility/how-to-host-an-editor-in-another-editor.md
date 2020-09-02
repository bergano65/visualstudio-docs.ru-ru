---
title: Как разместить редактор в другом редакторе | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4b4ff425feb22b5057a8d1a76b7f73b8932d9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204172"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Практическое руководство. Размещение редактора в другом редакторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В Visual Studio можно разместить один редактор внутри другого, указав окно размещения в качестве родительского окна. Для этого задайте параметры <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> и <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> в фрейме дочернего окна.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Настройка рамки окна для размещения редактора  
  
1. Назначьте редактор в качестве размещенного редактора, создав дочернюю область окна.  
  
     В этой области находится текст редактора.  
  
2. Создайте редактор размещения с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метода или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
3. Задайте <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> Свойства и <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> в реализации фрейма окна для размещенного редактора, передав эти свойства в качестве параметров в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> метод соответственно.  
  
     Если необходимо получить эти параметры, передайте эти свойства в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод.  
  
4. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод для вложенного редактора.  
  
     Редактор появится в области размещения содержащего редактора.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 **Конструктор приложений** в Visual Studio Team Edition для архитекторов — пример фрейма окна редактора, в котором размещается другой редактор. **Конструктор приложений** размещает другие конструкторы на правой панели. Панель конструктора (или страница **свойств** ) для каждого из содержащихся в нем конструкторов добавляется в фрейм окна, содержащий.

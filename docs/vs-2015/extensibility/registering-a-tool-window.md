---
title: Регистрация окна инструментов | Документация Майкрософт
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
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2ec947455383fd1d2a22ec98f8627ee53fbbad5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569773"
---
# <a name="registering-a-tool-window"></a>Регистрация окна инструментов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [регистрация окна инструментов](https://docs.microsoft.com/visualstudio/extensibility/registering-a-tool-window).  
  
Можно зарегистрировать с помощью средства windows <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> и  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## <a name="example"></a>Пример  
  
```csharp  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 В приведенном выше коде в <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> регистрирует окна инструментов PersistedWindowPane и DynamicWindowPane с помощью Visual Studio. Окно материализованных инструментов закреплено и с вкладками с **обозревателе решений**, и динамические окна по умолчанию, начальной позицией и размер. Динамическое окно становится временными, которое указывает, что она не была создана во время запуска. Записывает значение DontForceCreate в ключе ToolWindows в системном реестре. Дополнительные сведения см. в разделе [конфигурацию отображаемое окно средства](../extensibility/tool-window-display-configuration.md).


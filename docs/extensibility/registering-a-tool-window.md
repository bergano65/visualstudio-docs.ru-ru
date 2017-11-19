---
title: "Регистрация окно инструментов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79a2d2f1e9dc130fc280ce61ec282f30e55024ae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="registering-a-tool-window"></a>Регистрация окна инструментов
Можно зарегистрировать с помощью средства windows <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> и<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## <a name="example"></a>Пример  
  
```csharp  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 В представленном выше коде <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> регистрирует окна инструментов PersistedWindowPane и DynamicWindowPane вместе с Visual Studio. В окне инструментов сохраненного закрепления и с вкладками с **обозревателе решений**, и окно динамической присваивается значение по умолчанию, начиная с позиции и размера. Окно динамической становится временными, которое указывает, что она не была создана во время запуска. Записывает значение DontForceCreate в ключе ToolWindows в системном реестре. Дополнительные сведения см. в разделе [конфигурации отображения окна средства](../extensibility/tool-window-display-configuration.md).
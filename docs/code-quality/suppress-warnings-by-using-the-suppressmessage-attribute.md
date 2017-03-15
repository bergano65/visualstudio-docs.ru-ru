---
title: "Подавление предупреждений при помощи атрибута SuppressMessage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCFxCopTool.InputAssemblyFileName"
  - "VC.Project.VCFxCopTool.FxCopModuleSuppressionsFile"
  - "VC.Project.VCFxCopTool.FxCopUseTypeNameInSuppression"
  - "VC.Project.VCFxCopTool.OutputFile"
helpviewer_keywords: 
  - "анализ кода, подавление в исходном коде"
  - "анализ кода, SuppressMessage - атрибут"
  - "подавление в исходном коде"
  - "SuppressMessage - атрибут"
ms.assetid: a38c57a2-d29d-43c0-84ff-3308b2484ce6
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Подавление предупреждений при помощи атрибута SuppressMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Зачастую требуется указать, что предупреждение неприменимо, чтобы члены группы знали, что код прошел проверку и данное предупреждение было решено подавить.  Подавление в исходном коде \(ISS\) позволяет разработчику расположить атрибут, подавляющий предупреждение, рядом с местом, в котором создается предупреждение.  Такой атрибут ISS можно поместить непосредственно в исходном файле, либо можно воспользоваться контекстным меню в интегрированной среде разработки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## В этом подразделе  
  
|||  
|-|-|  
|[Общие сведения о подавлении в исходном коде](../code-quality/in-source-suppression-overview.md)|Сведения о подавлении ISS и его использовании в коде.|  
|[Практическое руководство. Отключение предупреждений при помощи пункта меню](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)|Сведения о подавлении предупреждений в интегрированной среде разработки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] при помощи контекстного меню.|  
  
## Связанные подразделы  
 [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
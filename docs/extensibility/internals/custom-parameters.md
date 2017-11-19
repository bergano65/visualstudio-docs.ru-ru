---
title: "Пользовательские параметры | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3f04251ea8141d07a52499beae46b2881814eec9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="custom-parameters"></a>Пользовательские параметры
Пользовательские параметры управляют работой мастер после запуска мастера. Связанные VSZ-файл предоставляет массив пользовательских параметров, которые упаковываются интегрированной средой разработки (IDE) и передавать мастеру как массив строк, при запуске мастера. После этого мастер анализирует массив строк и использует сведения для управления самой операции мастера. Таким образом мастер можно настроить функциональные возможности, в зависимости от содержимого VSZ-файле.  
  
 При запуске мастера параметров контекста, с другой стороны, определить состояние проекта. Дополнительные сведения см. в разделе [параметры контекста](../../extensibility/internals/context-parameters.md).  
  
 Ниже приведен пример файла VSZ с настраиваемыми параметрами:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 Автор VSZ-файл, добавляет значения параметров. Когда пользователь выбирает **новый проект** или **Добавление нового элемента** в меню "файл" или щелкнув правой кнопкой мыши проект в **обозревателе решений**, интегрированной среды разработки собирает эти значения в массиве строки. IDE, затем вызывает проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> метод с <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> флаг набор и вызовы проекта <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> метод, который отвечает за выполнение мастера и возвращая результат.  
  
 Мастер отвечает за синтаксический анализ массив строк и реагирования на строки, соответствующим образом. Таким образом путем реализации пользовательских параметров можно создать один мастер, который выполняет множество функций. Другими словами один мастер возможны три разных .vsz-файлы. Каждый файл передает разные наборы настраиваемых параметров для управления поведением мастера в различных ситуациях.  
  
 Дополнительные сведения см. в разделе [мастер (. Файл VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Контекстные параметры](../../extensibility/internals/context-parameters.md)   
 [Мастеры](../../extensibility/internals/wizards.md)   
 [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)
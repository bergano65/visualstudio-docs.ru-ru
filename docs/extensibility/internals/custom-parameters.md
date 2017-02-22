---
title: "Пользовательские параметры | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "мастера, пользовательские параметры"
  - "пользовательские параметры"
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Пользовательские параметры
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Пользовательские параметры контролируют работу мастера, после того как мастер запущен.  Связанный файл vsz предоставляет массив определенных пользователем параметров, упакованы интегрированной средой разработки \(ide\) и передаются в мастер как массив строк, если мастер будет запущен.  После этого мастер анализирует массив строк и использует сведения для наблюдения за фактическую операцию мастера.  Таким образом, мастер может настраивать функциональность в зависимости от содержимого файла vsz.  
  
 Параметры контекста, с другой стороны, определяющие состояние проекта, если мастер запущен.  Дополнительные сведения см. в разделе [Контекстные параметры](../../extensibility/internals/context-parameters.md).  
  
 Ниже приведен пример файла vsz, имеющий пользовательские параметры:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 Автор файла vsz добавляет значения параметров.  Когда пользователь выбирает **Создать проект** OR  **Добавление нового элемента** в меню " Файл " или щелкнув правой кнопкой мыши проект in  **Обозреватель решений**интегрированная среда разработки собирает эти значения в массиве строк.  Интегрированная среда разработки затем вызывает проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> метод с  <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> пометить набор, а проект называется  <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> метод, который отвечает за выполнение мастера и возвращения результата.  
  
 Мастер отвечает за анализ массив строк и работать со строками.  Таким образом, путем реализации пользовательских параметров можно создать один мастер, который выполняет разнообразные функции.  Иначе говоря, один мастер может иметь 3 различных файла vsz.  Каждый файл передает различные наборы пользовательских параметров для мониторинга расширения функциональности мастера в различных ситуациях.  
  
 Дополнительные сведения см. в разделе [Мастер \(. Файл VSZ\)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Контекстные параметры](../../extensibility/internals/context-parameters.md)   
 [Мастера](../../extensibility/internals/wizards.md)   
 [Мастер \(. Файл VSZ\)](../../extensibility/internals/wizard-dot-vsz-file.md)
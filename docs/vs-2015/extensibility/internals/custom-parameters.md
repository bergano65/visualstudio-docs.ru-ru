---
title: Пользовательские параметры | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a595861be835ec1aaa7079b3e3fe1962d5055e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154998"
---
# <a name="custom-parameters"></a>Настраиваемые параметры
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пользовательские параметры управляют работой мастера после запуска мастера. Связанный VSZ-файл предоставляет массив определяемых пользователем параметров, которые упаковываются интегрированной средой разработки (IDE) и передаются мастеру как массив строк при запуске мастера. Затем мастер анализирует массив строк и использует эти сведения для управления фактической работой мастера. Таким образом, мастер может настроить функциональные возможности в зависимости от содержимого файла VSZ.  
  
 Параметры контекста, с другой стороны, определяют состояние проекта при запуске мастера. Дополнительные сведения см. в разделе [Параметры контекста](../../extensibility/internals/context-parameters.md).  
  
 Ниже приведен пример файла VSZ с пользовательскими параметрами.  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 Автор файла VSZ добавляет значения параметров. Когда пользователь выбирает **Новый проект** или **добавляет новый элемент** в меню файл или щелкает правой кнопкой мыши проект в **Обозреватель решений**, интегрированная среда разработки собирает эти значения в массив строк. Затем интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> метод проекта с <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> установленным флагом, и проект вызывает <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> метод, отвечающий за запуск мастера и возврат результата.  
  
 Мастер отвечает за синтаксический анализ массива строк и правильное взаимодействие со строками. Таким образом, реализуя пользовательские параметры, можно создать один мастер, выполняющий различные функции. Другими словами, один мастер может иметь три разных VSZ-файла. Каждый файл передает различные наборы пользовательских параметров для управления поведением мастера в различных ситуациях.  
  
 Дополнительные сведения см. в разделе [Мастер (. VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Параметры контекста](../../extensibility/internals/context-parameters.md)   
 [Мастера](../../extensibility/internals/wizards.md)   
 [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)

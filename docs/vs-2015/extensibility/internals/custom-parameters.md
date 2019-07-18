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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154998"
---
# <a name="custom-parameters"></a>Настраиваемые параметры
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пользовательские параметры управляют работой мастера, после запуска мастера. Связанные VSZ-файл предоставляет целый ряд определяемых пользователем параметров, которые упаковываются по интегрированной среде разработки (IDE) и передан мастеру, как массив строк, при запуске данного мастера. Затем мастер анализирует массив строк и использует сведения для управления самой операции мастера. Таким образом мастер можно настроить функциональные возможности в зависимости от содержимого VSZ-файле.  
  
 Параметры контекста, с другой стороны, определять состояние проекта при запуске данного мастера. Дополнительные сведения см. в разделе [параметры контекста](../../extensibility/internals/context-parameters.md).  
  
 Ниже приведен пример VSZ-файл, содержащий пользовательские параметры.  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 Автор VSZ-файл добавляет значения параметров. Когда пользователь выбирает **новый проект** или **Добавление нового элемента** в меню "файл" или щелкнув правой кнопкой мыши проект в **обозревателе решений**, интегрированной среды разработки собирает следующие значения в массив строки. Интегрированная среда разработки, затем вызывает проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> метод с <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> флаг набора и вызываемого проектом <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> метод, который отвечает за запуск мастера и возвращает результат.  
  
 Мастер отвечает за синтаксический анализ массив строк и действует соответствующим образом на строки. Таким образом путем реализации настраиваемых параметров можно создать один мастер, который выполняет множество функций. Другими словами один-единственный мастер может иметь три разных .vsz-файлы. Каждый файл передает различный набор настраиваемых параметров для управления поведением мастера в различных ситуациях.  
  
 Дополнительные сведения см. в разделе [мастер (. Файл VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Параметры контекста](../../extensibility/internals/context-parameters.md)   
 [Мастеры](../../extensibility/internals/wizards.md)   
 [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)

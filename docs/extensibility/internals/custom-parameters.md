---
title: Пользовательские параметры | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e86c2f48365f93c924b15ae8d696d53d3f4bb16
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596664"
---
# <a name="custom-parameters"></a>Пользовательские параметры
Пользовательские параметры управляют работой мастера, после запуска мастера. Связанный с ним *.vsz* файл предоставляет целый ряд определяемых пользователем параметров, которые упаковываются по интегрированной среде разработки (IDE) и передан мастеру, как массив строк, при запуске данного мастера. Затем мастер анализирует массив строк и использует сведения для управления самой операции мастера. Таким образом, мастер можно настроить функциональные возможности в зависимости от содержимого *.vsz* файл.

 Параметры контекста, с другой стороны, определять состояние проекта при запуске данного мастера. Дополнительные сведения см. в разделе [параметры контекста](../../extensibility/internals/context-parameters.md).

 Ниже приведен пример *.vsz* файл, содержащий пользовательские параметры:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 Автор *.vsz* файл добавляет значения параметров. Когда пользователь выбирает **новый проект** или **Добавление нового элемента** на **файл** меню или щелкнув правой кнопкой мыши проект в **обозревателе решений**, интегрированной среды разработки собирает эти значения в массиве строк. Интегрированная среда разработки, затем вызывает проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> метод с <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> флаг набора и вызываемого проектом <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> метод, который отвечает за запуск мастера и возвращает результат.

 Мастер отвечает за синтаксический анализ массив строк и действует соответствующим образом на строки. Таким образом путем реализации настраиваемых параметров можно создать один мастер, который выполняет множество функций. Другими словами, один-единственный мастер может иметь три разных *.vsz* файлов. Каждый файл передает различный набор настраиваемых параметров для управления поведением мастера в различных ситуациях.

 Дополнительные сведения см. в разделе [файл мастера (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Контекстные параметры](../../extensibility/internals/context-parameters.md)
- [Мастера](../../extensibility/internals/wizards.md)
- [Файл мастера (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
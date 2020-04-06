---
title: Пользовательские параметры Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd52a49daa7d57a21d8cb0896f7108efa09e32b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708936"
---
# <a name="custom-parameters"></a>Пользовательские параметры
Пользовательские параметры контролируют работу мастера после начала мастера. Связанный файл *.vsz* предоставляет массив параметров, определяемых пользователем, которые упакованы в интегрированную среду разработки (IDE) и передаются мастеру в виде массива строк при начале работы мастера. Затем мастер разбирает массив строк и использует информацию для управления фактической работой мастера. Таким образом, мастер может настроить функциональность в зависимости от содержимого файла *.vsz.*

 Параметры контекста, с другой стороны, определяют состояние проекта при начале работы мастера. Для получения дополнительной [информации см.](../../extensibility/internals/context-parameters.md)

 Ниже приводится пример файла *.vsz,* который имеет пользовательские параметры:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 Автор файла *.vsz* добавляет значения параметров. Когда пользователь выбирает **новый проект** или **добавляет новый элемент** в меню **файла** или при правильном нажатии на проект в **Solution Explorer,** IDE собирает эти значения в массив строк. Затем IDE вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> метод проекта с <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> набором флага, <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> а проект называет метод, отвечающий за запуск мастера и возвращение результата.

 Мастер отвечает за разбор массив строк и соответствующее действие на строках. Таким образом, реализуя пользовательские параметры, можно создать одного мастера, который выполняет различные функции. Другими словами, один мастер может иметь три различных файла *.vsz.* Каждый файл проходит различные наборы пользовательских параметров для управления поведением мастера в различных ситуациях.

 Для получения дополнительной [Wizard (.vsz) file](../../extensibility/internals/wizard-dot-vsz-file.md)информации см.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Контекстные параметры](../../extensibility/internals/context-parameters.md)
- [Мастера](../../extensibility/internals/wizards.md)
- [Файл Мастера (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

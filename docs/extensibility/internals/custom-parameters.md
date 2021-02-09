---
title: Пользовательские параметры | Документация Майкрософт
description: Узнайте, как создавать настраиваемые параметры, управляющие работой мастера после запуска мастера, изменяя VSZ-файл.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1b4927e63bec93fbe7b6730e131a0893372aa70d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902970"
---
# <a name="custom-parameters"></a>Пользовательские параметры
Пользовательские параметры управляют работой мастера после запуска мастера. Связанный *VSZ* -файл предоставляет массив определяемых пользователем параметров, которые упаковываются интегрированной средой разработки (IDE) и передаются мастеру как массив строк при запуске мастера. Затем мастер анализирует массив строк и использует эти сведения для управления фактической работой мастера. Таким образом, мастер может настроить функциональные возможности в зависимости от содержимого файла *VSZ* .

 Параметры контекста, с другой стороны, определяют состояние проекта при запуске мастера. Дополнительные сведения см. в разделе [Параметры контекста](../../extensibility/internals/context-parameters.md).

 Ниже приведен пример файла *VSZ* с пользовательскими параметрами.

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 Автор файла *VSZ* добавляет значения параметров. Когда пользователь выбирает **Новый проект** или **добавляет новый элемент** в меню **файл** или щелкает правой кнопкой мыши проект в **Обозреватель решений**, интегрированная среда разработки собирает эти значения в массив строк. Затем интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> метод проекта с <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> установленным флагом, и проект вызывает <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> метод, отвечающий за запуск мастера и возврат результата.

 Мастер отвечает за синтаксический анализ массива строк и правильное взаимодействие со строками. Таким образом, реализуя пользовательские параметры, можно создать один мастер, выполняющий различные функции. Другими словами, один мастер может иметь три разных *VSZ* -файла. Каждый файл передает различные наборы пользовательских параметров для управления поведением мастера в различных ситуациях.

 Дополнительные сведения см. в разделе [Мастер (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>См. также раздел
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Контекстные параметры](../../extensibility/internals/context-parameters.md)
- [Мастера](../../extensibility/internals/wizards.md)
- [Файл мастера (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)

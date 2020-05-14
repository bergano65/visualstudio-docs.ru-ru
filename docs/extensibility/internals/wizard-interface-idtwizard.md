---
title: Интерфейс мастера (IDTWizard) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1c8d728a76097321e4e1f16640cab97599d6ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703279"
---
# <a name="wizard-interface-idtwizard"></a>Интерфейс мастера (IDTWizard)
Интегрированная среда разработки (IDE) использует <xref:EnvDTE.IDTWizard> интерфейс для связи с мастерами. Волшебники должны реализовать этот интерфейс, чтобы быть установленным в IDE.

 Метод <xref:EnvDTE.IDTWizard.Execute%2A> является единственным методом, <xref:EnvDTE.IDTWizard> связанным с интерфейсом. Мастера реализуют этот метод, и IDE вызывает метод на интерфейсе. В следующем примере показана подпись метода.

```
/* IDTWizard Method */
STDMETHOD(Execute)(THIS_
   /* [in] */ IDispatch *Application,
   /* [in] */ long hwndOwner,
   /* [in] */ SAFEARRAY * *ContextParams,
   /* [in] */ SAFEARRAY * *CustomParams,
   /* [out] [in] */ wizardResult *RetVal
   );
```

 Механизм запуска аналогичен как для **новых проектов,** так и для мастеров **добавления нового элемента.** Для начала вы называете интерфейс, <xref:EnvDTE.IDTWizard> определенный в Dteinternal.h. Разница лишь в наборе контекста и пользовательских параметров, которые передаются интерфейсу при вызове интерфейса.

 Ниже приводится <xref:EnvDTE.IDTWizard> информация о интерфейсе, который [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] мастера должны реализовать для работы в IDE. IDE называет <xref:EnvDTE.IDTWizard.Execute%2A> метод на мастере, передавая его следующим образом:

- Объект DTE

     Объект DTE является корнем модели автоматизации.

- Ручка к окну диалогового окна, `hwndOwner ([in] long)`как показано в сегменте кода, .

     Мастер использует `hwndOwner` это в качестве родительского для диалогового окна мастера.

- Параметры контекста перешли в интерфейс в качестве варианта для `[in] SAFEARRAY (VARIANT)* ContextParams`SAFEARRAY, как показано в сегменте кода, .

     Параметры контекста содержат массив значений, относящихся к типу запуска мастера и текущему состоянию проекта. IDE передает параметры контекста мастеру. Для получения дополнительной [информации см.](../../extensibility/internals/context-parameters.md)

- Пользовательские параметры перешли в интерфейс в качестве варианта для `[in] SAFEARRAY (VARIANT)* CustomParams`SAFEARRAY, как показано в сегменте кода, .

     Пользовательские параметры содержат массив параметров, определяемых пользователем. Файл .vsz передает пользовательские параметры в IDE. Значения определяются заявлениями. `Param=` Для получения дополнительной [информации см.](../../extensibility/internals/custom-parameters.md)

- Значения возврата для интерфейса

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>См. также
- [Параметры контекста](../../extensibility/internals/context-parameters.md)
- [Настраиваемые параметры](../../extensibility/internals/custom-parameters.md)
- [Мастера](../../extensibility/internals/wizards.md)
- [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)

---
title: Интерфейс мастера (Идтвизард) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f571fbd0a68ddbf56b637071ac250159461f61d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721532"
---
# <a name="wizard-interface-idtwizard"></a>Интерфейс мастера (IDTWizard)
Интегрированная среда разработки (IDE) использует интерфейс <xref:EnvDTE.IDTWizard> для взаимодействия с мастерами. Мастера должны реализовать этот интерфейс для установки в интегрированной среде разработки.

 Метод <xref:EnvDTE.IDTWizard.Execute%2A> является единственным методом, связанным с интерфейсом <xref:EnvDTE.IDTWizard>. Мастера реализуют этот метод, и интегрированная среда разработки вызывает метод для интерфейса. В следующем примере показана сигнатура метода.

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

 Механизм запуска аналогичен для мастеров " **Новый проект** " и " **Добавление новых элементов** ". Для запуска либо вызывается интерфейс <xref:EnvDTE.IDTWizard>, определенный в Дтеинтернал. h. Единственное различие — это набор контекстных и пользовательских параметров, которые передаются в интерфейс при вызове интерфейса.

 Ниже приведена информация о <xref:EnvDTE.IDTWizard> интерфейсе, который мастер должен реализовать для работы в интегрированной среде разработки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Интегрированная среда разработки вызывает метод <xref:EnvDTE.IDTWizard.Execute%2A> в мастере, передавая ему следующее:

- Объект DTE

     Объект DTE является корнем модели автоматизации.

- Маркер для диалогового окна окна, как показано в сегменте кода `hwndOwner ([in] long)`.

     Мастер использует этот `hwndOwner` в качестве родительского для диалогового окна мастера.

- Контекстные параметры передаются в интерфейс как Variant для SAFEARRAY, как показано в сегменте кода `[in] SAFEARRAY (VARIANT)* ContextParams`.

     Параметры контекста содержат массив значений, относящихся к типу запуска мастера и текущему состоянию проекта. Интегрированная среда разработки передает параметры контекста в мастер. Дополнительные сведения см. в разделе [Параметры контекста](../../extensibility/internals/context-parameters.md).

- Пользовательские параметры, передаваемые интерфейсу как Variant для SAFEARRAY, как показано в сегменте кода `[in] SAFEARRAY (VARIANT)* CustomParams`.

     Пользовательские параметры содержат массив определяемых пользователем параметров. VSZ-файл передает в интегрированную среду разработки пользовательские параметры. Значения определяются инструкциями `Param=`. Дополнительные сведения см. в разделе [пользовательские параметры](../../extensibility/internals/custom-parameters.md).

- Возвращаемые значения для интерфейса

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>См. также
- [Контекстные параметры](../../extensibility/internals/context-parameters.md)
- [Настраиваемые параметры](../../extensibility/internals/custom-parameters.md)
- [Мастера](../../extensibility/internals/wizards.md)
- [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)
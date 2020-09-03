---
title: Интерфейс мастера (Идтвизард) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 78867fa94851e373ae4d47cd82cd1084a941638c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180354"
---
# <a name="wizard-interface-idtwizard"></a>Интерфейс мастера (IDTWizard)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Интегрированная среда разработки (IDE) использует <xref:EnvDTE.IDTWizard> интерфейс для взаимодействия с мастерами. Мастера должны реализовать этот интерфейс для установки в интегрированной среде разработки.  
  
 <xref:EnvDTE.IDTWizard.Execute%2A>Метод является единственным методом, связанным с <xref:EnvDTE.IDTWizard> интерфейсом. Мастера реализуют этот метод, и интегрированная среда разработки вызывает метод для интерфейса. В следующем примере показана сигнатура метода.  
  
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
  
 Механизм запуска аналогичен для мастеров " **Новый проект** " и " **Добавление новых элементов**". Для запуска можно вызвать <xref:EnvDTE.IDTWizard> интерфейс, определенный в дтеинтернал. h. Единственное различие — это набор контекстных и пользовательских параметров, которые передаются в интерфейс при вызове интерфейса.  
  
 Ниже приведена информация о <xref:EnvDTE.IDTWizard> интерфейсе, который мастер должен реализовать для работы в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среде разработки. Интегрированная среда разработки вызывает <xref:EnvDTE.IDTWizard.Execute%2A> метод в мастере, передавая ему следующее:  
  
- Объект DTE  
  
     Объект DTE является корнем модели автоматизации.  
  
- Маркер для диалогового окна окна, как показано в сегменте кода `hwndOwner ([in] long)` .  
  
     Мастер использует его `hwndOwner` в качестве родительского для диалогового окна мастера.  
  
- Контекстные параметры передаются в интерфейс как Variant для SAFEARRAY, как показано в сегменте кода `[in] SAFEARRAY (VARIANT)* ContextParams` .  
  
     Параметры контекста содержат массив значений, относящихся к типу запуска мастера и текущему состоянию проекта. Интегрированная среда разработки передает параметры контекста в мастер. Дополнительные сведения см. в разделе [Параметры контекста](../../extensibility/internals/context-parameters.md).  
  
- Пользовательские параметры, передаваемые интерфейсу как Variant для SAFEARRAY, как показано в сегменте кода `[in] SAFEARRAY (VARIANT)* CustomParams` .  
  
     Пользовательские параметры содержат массив определяемых пользователем параметров. VSZ-файл передает в интегрированную среду разработки пользовательские параметры. Значения определяются `Param=` инструкциями. Дополнительные сведения см. в разделе [пользовательские параметры](../../extensibility/internals/custom-parameters.md).  
  
- Возвращаемые значения для интерфейса  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Параметры контекста](../../extensibility/internals/context-parameters.md)   
 [Пользовательские параметры](../../extensibility/internals/custom-parameters.md)   
 [Мастера](../../extensibility/internals/wizards.md)   
 [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)

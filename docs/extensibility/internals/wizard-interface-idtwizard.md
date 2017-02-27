---
title: "Интерфейс мастера (IDTWizard) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDTWizard"
  - "мастера, интерфейс"
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс мастера (IDTWizard)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Интегрированная среда разработки \(ide\) <xref:EnvDTE.IDTWizard> интерфейс для взаимодействия с помощью мастеров.  Мастера, должны реализовать этот интерфейс в результате чего устанавливается в интегрированной среде разработки.  
  
 <xref:EnvDTE.IDTWizard.Execute%2A> метод единственный метод, связанный с  <xref:EnvDTE.IDTWizard> интерфейс.  Мастеры реализуют этот метод и интегрированная среда разработки вызывает метод в интерфейсе.  В следующем примере показана сигнатура метода.  
  
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
  
 Механизм аналогичен для обоих start **Создать проект** и  **Добавление нового элемента** мастера.  Для запуска то вызывается метод <xref:EnvDTE.IDTWizard> интерфейс, указанный в Dteinternal.h.  Единственное различие заключается в том, что набор параметров контекста, и пользовательские события, которые передаются интерфейсу, когда интерфейс вызывается.  
  
 Следующие сведения описывают <xref:EnvDTE.IDTWizard> интерфейс, который должны реализовывать для работы в мастерах  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированная среда разработки.  Интегрированная среда разработки вызывает <xref:EnvDTE.IDTWizard.Execute%2A> метод в мастере, передав следующие действия:  
  
-   Объект DTE  
  
     Объект DTE является корневым объектом модели автоматизации.  
  
-   Дескриптор окна, как показано диалоговое окно в сегменте кода `hwndOwner ([in] long)`.  
  
     Мастер использует эти `hwndOwner` в качестве родительского для диалогового окна мастера.  
  
-   Контекстные параметры, передаваемые интерфейсу как вариант, SAFEARRAY, как показано в сегменте кода `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Контекстные параметры содержат массив значений, которые относятся к типу, работу мастера, а текущее состояние проекта.  Интегрированная среда разработки передает параметры контекста в мастер.  Дополнительные сведения см. в разделе [Контекстные параметры](../../extensibility/internals/context-parameters.md).  
  
-   Пользовательские параметры, передаваемые интерфейсу как вариант, SAFEARRAY, как показано в сегменте кода `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Пользовательские параметры содержат массив определенных пользователем параметров.  Vsz\-файл передает пользовательские параметры в интегрированной среде разработки.  Значения определяются `Param=` выписки.  Дополнительные сведения см. в разделе [Пользовательские параметры](../../extensibility/internals/custom-parameters.md).  
  
-   Возвращаемые значения для интерфейса  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## См. также  
 [Контекстные параметры](../../extensibility/internals/context-parameters.md)   
 [Пользовательские параметры](../../extensibility/internals/custom-parameters.md)   
 [Мастера](../../extensibility/internals/wizards.md)   
 [Мастер \(. Файл VSZ\)](../../extensibility/internals/wizard-dot-vsz-file.md)
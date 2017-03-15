---
title: "Поддержка модели автоматизации для страницы параметров | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Сервис Параметры-страницы [Visual Studio SDK] Поддержка автоматизации"
  - "Создание страницы средств автоматизации [Visual Studio SDK]"
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# Поддержка модели автоматизации для страницы параметров
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Пакеты VSPackage можно предоставить пользовательский **Параметры** диалоговых окон для **средства** \(страницы параметров средств\) в меню [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и их можно сделать доступными для модели автоматизации.  
  
## Сервис Параметры\-страницы  
 Для создания **Сервис Параметры** страницы, VSPackage должен предоставить реализацию пользовательского элемента управления, возвращается к среде через реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод \(или управляемого кода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод\).  
  
 Это необязательно, но настоятельно рекомендуется, чтобы разрешить доступ к этой новой странице через модель автоматизации. Для этого выполните следующие шаги:  
  
1.  Расширить <xref:EnvDTE._DTE.Properties%2A> объекта путем реализации интерфейса IDispatch производного объекта.  
  
2.  Вернуть реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод \(или для управляемого кода <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> метод\) на объект производного IDispatch.  
  
3.  При вызове объекта\-получателя автоматизации <xref:EnvDTE._DTE.Properties%2A> метод пользовательского **параметр** на странице свойств в среде используется <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> способ получения пользовательского **Сервис Параметры** реализация автоматизации страницы.  
  
4.  Объект автоматизации VSPackage затем используется для предоставления каждого <xref:EnvDTE.Property> возвращаемый <xref:EnvDTE._DTE.Properties%2A>.  
  
 Пример реализации пользовательской странице параметров средств в разделе [Примеры VSSDK](../../misc/vssdk-samples.md).  
  
## См. также  
 [Предоставление доступа к объектам проекта](../../extensibility/internals/exposing-project-objects.md)
---
title: "Поддержка модели автоматизации для страницы параметров | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ca9031e623ec7009d4f489931871f093f4c05d5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="automation-support-for-options-pages"></a>Поддержка модели автоматизации для страницы параметров
Пакеты VSPackage могут предоставить пользовательские **параметры** диалоговых окон для **средства** (страницы параметров средств) в меню [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и их можно сделать доступными в модели автоматизации.  
  
## <a name="tools-options-pages"></a>Страницы параметров средств  
 Для создания **Сервис — Параметры** страницы, VSPackage должен предоставить реализацию пользовательского элемента управления, возвращается в среду через реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод (или для управляемого кода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод).  
  
 Это необязательно, но настоятельно рекомендуется, чтобы разрешить доступ к этой новой странице через модель автоматизации. Это можно сделать через следующую последовательность шагов:  
  
1.  Расширить <xref:EnvDTE._DTE.Properties%2A> объекта путем реализации производным интерфейса IDispatch объекта.  
  
2.  Вернуть реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод (или для управляемого кода <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> метод) на объект производного интерфейса IDispatch.  
  
3.  При вызове объекта-получателя автоматизации <xref:EnvDTE._DTE.Properties%2A> метода в пользовательском **параметр** страницу свойств в среде используется <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод, чтобы получить пользовательский **Сервис — Параметры** автоматизации страницы Реализация.  
  
4.  Объект автоматизации VSPackage затем используется для предоставления каждого <xref:EnvDTE.Property> возвращенных <xref:EnvDTE._DTE.Properties%2A>.  
  
 Пример реализации пользовательской страницы параметров средств см. в разделе [примеры VSSDK](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>См. также  
 [Предоставление доступа к объектам проекта](../../extensibility/internals/exposing-project-objects.md)
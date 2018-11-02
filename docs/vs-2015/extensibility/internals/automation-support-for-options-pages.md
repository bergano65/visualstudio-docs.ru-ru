---
title: Поддержка автоматизации страниц параметров | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ded80c0bcb7ac8246d1ac620aa936d63ecb3b04d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902377"
---
# <a name="automation-support-for-options-pages"></a>Поддержка автоматизации страниц параметров
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пакеты VSPackage могут предоставлять пользовательскую **параметры** диалоговых окон для **средства** меню (страницы параметров средств) в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и их можно сделать доступными для модели автоматизации.  
  
## <a name="tools-options-pages"></a>Страницы параметров средств  
 Для создания **Сервис-Параметры** странице VSPackage необходимо предоставить реализацию пользовательского элемента управления, возвращается в среду через реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метода (или для управляемого кода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод).  
  
 Это необязательно, но настоятельно рекомендуется, чтобы разрешить доступ к этой новой странице с помощью модели автоматизации. Это можно сделать следующие этапы:  
  
1. Расширить <xref:EnvDTE._DTE.Properties%2A> объекта путем реализации производным интерфейса IDispatch объекта.  
  
2. Возвращают реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод (или для управляемого кода <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> метод) на объект производного IDispatch.  
  
3. Когда потребитель автоматизации вызывает <xref:EnvDTE._DTE.Properties%2A> метода в пользовательском **параметр** страницу свойств в среде используется <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод, чтобы получить пользовательский **Сервис-Параметры** автоматизации страницы Реализация.  
  
4. Объект автоматизации из VSPackage затем используется для предоставления каждой <xref:EnvDTE.Property> возвращаемый <xref:EnvDTE._DTE.Properties%2A>.  
  
   Пример реализации пользовательской страницы параметров средств см. в разделе [примеры VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>См. также  
 [Предоставление доступа к объектам проекта](../../extensibility/internals/exposing-project-objects.md)


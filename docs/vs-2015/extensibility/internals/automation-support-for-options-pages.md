---
title: Поддержка автоматизации для страниц параметров | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cb2634f5a16c62222cf360065cae0c22aef6667
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157240"
---
# <a name="automation-support-for-options-pages"></a>Поддержка автоматизации страниц параметров
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пакеты VSPackage могут предоставлять диалоговые окна настраиваемых **параметров** в меню **Сервис** (Сервис Параметры страницы) в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и предоставлять их для модели автоматизации.  
  
## <a name="tools-options-pages"></a>Страницы параметров средств  
 Для создания страницы **параметров средств** пакет VSPackage должен предоставить реализацию пользовательского элемента управления, возвращаемую в среду, с помощью реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метода VSPackage (или управляемого кода для <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метода).  
  
 Это необязательно, но настоятельно рекомендуется, чтобы разрешить доступ к этой новой странице через модель автоматизации. Это можно сделать, выполнив следующие действия.  
  
1. Расширьте <xref:EnvDTE._DTE.Properties%2A> объект с помощью реализации объекта, производного от IDispatch.  
  
2. Возврат реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метода (или для управляемого кода <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> метода) в объект, производный от IDispatch.  
  
3. Когда потребитель автоматизации вызывает <xref:EnvDTE._DTE.Properties%2A> метод на странице настраиваемого свойства **параметра** , среда использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод для получения реализации автоматизации страницы настраиваемых **средств** .  
  
4. Затем объект автоматизации VSPackage используется для предоставления каждого <xref:EnvDTE.Property> возвращаемого объекта <xref:EnvDTE._DTE.Properties%2A> .  
  
   Пример реализации настраиваемой страницы параметров средств см. в разделе [VSSDK Samples](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>См. также:  
 [Предоставление доступа к объектам проекта](../../extensibility/internals/exposing-project-objects.md)

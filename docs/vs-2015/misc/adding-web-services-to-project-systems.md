---
title: Добавление веб-служб в системы проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: f5b192be8e5f68ad9314fe08fff963c032013cb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002665"
---
# <a name="adding-web-services-to-project-systems"></a>Добавление веб-служб в системы проектов
Веб-службы XML — это, в общем, ресурсы с адресацией по URL-адресам, которые возвращают программную информацию в систему проектов с помощью протокола SOAP. Веб-службы можно интегрировать в систему проектов VSPackage с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> интерфейса.  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>Добавление веб-службы в систему проектов  
  
1. Вызовите `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> интерфейс через <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> службу.  
  
2. Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> . Если параметр передается `pDiscoverySession` как `NULL` , сеанс обнаружения создается для вас, а сеанс кэшируется, чтобы он был доступен для последующего использования <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> интерфейсом. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> метод возвращает указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2> .  
  
3. Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> . Передайте объект автоматизации для папки Web Service References в качестве `pUnkWebReferenceFolder` параметра. Затем среда Visual Studio проверяет, существует ли уже веб-служба. Если веб-служба отсутствует, среда загружает и добавляет веб-службу в папку и все дополнительные файлы (например, WSDL-файлы) в дочерние узлы папки.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>
---
title: "Добавление веб-служб в системы проектов | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "системы проектов, добавление веб-служб"
  - "веб-службы, добавление в системы проектов VSPackage"
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Добавление веб-служб в системы проектов
Xml\-веб\-службы обычно URL\-адрес\-addressable ресурсы, которые возвращают программный сведения в системе проектов с использованием протокола SOAP \(simple SOAP\).  Можно интегрировать веб\-службы к системе проектов с помощью VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> интерфейс.  
  
### Чтобы добавить веб\-службу в системе проектов  
  
1.  Вызов `QueryService` для  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> интерфейс до конца  <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> служба.  
  
2.  Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>.  При передаче in `pDiscoverySession` параметр как  `NULL`сеанс представления создан, и сеанс будет кэширован, чтобы он будет доступен для последующего использования  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> интерфейс.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> возвращает указатель на метод  <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>.  
  
3.  Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A>.  Передайте объект автоматизации для папки ссылок веб\-службы как `pUnkWebReferenceFolder` параметр.  Среда Visual Studio, затем проверяет, если веб\-службы уже существует.  Если веб\-служба не существует, среда загрузил и добавляет веб\-службы в папке и всем дополнительным файлам \(например, файлы wsdl\) к дочерним узлам папки.  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>
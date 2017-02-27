---
title: "Сведения об источнике управления среды выполнения | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Система управления версиями [Visual Studio SDK], сведения о времени выполнения"
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Сведения об источнике управления среды выполнения
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Проект будет добавлен к системе управления версиями, когда пользователь добавляет файл проекта к системе управления версиями или контроллер ole\-автоматизации, как мастер.  Проект не определяет для себя, что он находится в системе управления версиями; он поддерживает систему управления версиями, но должен быть добавлен на нее вручную.  
  
## Регистрация с пакетом системы управления версиями  
 Если файл в проекте будет добавлен к системе управления версиями, вызовы среды <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> предоставить возможность 4 непрозрачных строки, используемые как файлы cookie системой управления версиями.  Храните эти строки в файле проекта.  Эти строки должны быть переданы в заглушке системы управления версиями \(компонент Visual Studio, который управляет пакетами системы управления версиями\) при запуске проекта путем вызова метода типа <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>.  Это, в свою очередь, загружает соответствующий пакет системы управления версиями и переадресует вызов реализации `IVsSccManager2::RegisterSccProject`.  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)
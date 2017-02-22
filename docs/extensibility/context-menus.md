---
title: "Контекстные меню | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - контекстные меню"
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Контекстные меню
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Контекстные меню отображаются, когда пользователь щелкнул правой кнопкой мыши в активной области клиентской области и clear при отпускании правой кнопки мыши.  
  
## Контекстные меню редактора  
 Можно перехватывать `ECMD_SHOWCONTEXTMENU`ваша служба языка может отслеживать контекстные меню, которые будут отображаться в редакторе.  Для отображения собственного контекстного меню, настройте эту команду, когда оно передается в модель <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>путем вызова  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  Если не обработать эту команду, интегрированная среда разработки отображает стандартное контекстное меню, предоставляемое для редактора.  Также можно контролировать содержимое контекстного меню для каждого в\-метки.  Дополнительные сведения см. в разделах [С помощью текстовых маркеров с API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md) и [Перехват команд службы языка прежних версий](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## См. также  
 [Разработка службы языка](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)
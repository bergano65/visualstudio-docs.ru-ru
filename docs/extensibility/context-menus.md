---
title: Контекстные меню | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa957e949127663eca7d4e619919edcc07c7a29b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="context-menus"></a>Контекстные меню
Контекстные меню отображаются, когда пользователь щелкает правой кнопкой мыши в активной области, клиентской области и снимите при отпускании правой кнопки мыши.  
  
## <a name="editor-context-menus"></a>Контекстные меню редактора  
 Перехватывая `ECMD_SHOWCONTEXTMENU`, службе языка можно управлять контекстные меню, которые будут отображаться в редакторе. Чтобы отобразить контекстное меню, обрабатывать эту команду при передаче в вашей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Если эта команда не обрабатывают, интегрированной среды разработки отображает стандартное контекстное меню, предоставляемых для редактора. Также можно управлять содержимым на основе маркер контекстного меню. Дополнительные сведения об этом см. в разделе [с помощью текстовых маркеров с помощью прежних версий API](../extensibility/using-text-markers-with-the-legacy-api.md) и [перехват команды службы языка для прежних версий](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>См. также  
 [Разработке службы языка для прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)
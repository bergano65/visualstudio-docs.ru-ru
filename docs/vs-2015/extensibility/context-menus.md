---
title: Контекстные меню | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9baab8ef64fa1952eff138165f608e25960c8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184265"
---
# <a name="context-menus"></a>Контекстные меню
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Контекстные меню отображаются, когда пользователь щелкает правой кнопкой мыши активную область клиентской области и очищается при отпускании правой кнопки мыши.  
  
## <a name="editor-context-menus"></a>Контекстные меню редактора  
 С помощью перехвата `ECMD_SHOWCONTEXTMENU` языковая служба может управлять контекстными меню, которые будут отображаться в редакторе. Чтобы отобразить собственное контекстное меню, обработайте эту команду при передаче в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> . Если эта команда не обрабатывается, в интегрированной среде разработки отображается стандартное контекстное меню, предоставленное для редактора. Можно также управлять содержимым контекстного меню для каждого маркера. Дополнительные сведения см. в разделе [Использование текстовых маркеров с устаревшим API](../extensibility/using-text-markers-with-the-legacy-api.md) и [перехват команд языковой службы прежних версий](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>См. также:  
 [Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)

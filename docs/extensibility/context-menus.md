---
title: Контекстные меню | Документация Майкрософт
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
ms.openlocfilehash: afd67578bee63408b50e402fb0bd8b29be3fc6eb
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232537"
---
# <a name="context-menus"></a>Контекстные меню
Контекстные меню отображаются, когда пользователь щелкает правой кнопкой мыши в активную область клиентской области и очистить при отпускании правой кнопки мыши.  
  
## <a name="editor-context-menus"></a>Контекстные меню редактора  
 Перехватывая `ECMD_SHOWCONTEXTMENU`, языковой службы можно управлять контекстные меню, которые будут отображаться в редакторе. Чтобы отобразить собственное контекстное меню, обрабатывать эту команду при передаче в вашей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Если эта команда не обрабатывают, интегрированная среда разработки отображает стандартное контекстное меню, предоставленный для редактора. Также можно управлять содержимым контекстного меню на основе каждого маркера. Дополнительные сведения об этом см. в разделе [использовать текстовые метки с устаревшего API](../extensibility/using-text-markers-with-the-legacy-api.md) и [перехват команд службы прежней версией языка](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>См. также  
 [Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)
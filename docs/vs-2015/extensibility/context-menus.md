---
title: Контекстные меню | Документация Майкрософт
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
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4b53174776b93d94c38982a430db3213ba184b9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207733"
---
# <a name="context-menus"></a>Контекстные меню
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Контекстные меню отображаются, когда пользователь щелкает правой кнопкой мыши в активную область клиентской области и очистить при отпускании правой кнопки мыши.  
  
## <a name="editor-context-menus"></a>Контекстные меню редактора  
 Перехватывая `ECMD_SHOWCONTEXTMENU`, языковой службы можно управлять контекстные меню, которые будут отображаться в редакторе. Чтобы отобразить собственное контекстное меню, обрабатывать эту команду при передаче в вашей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Если эта команда не обрабатывают, интегрированная среда разработки отображает стандартное контекстное меню, предоставленный для редактора. Также можно управлять содержимым контекстного меню на основе каждого маркера. Дополнительные сведения об этом см. в разделе [с помощью меток текста с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md) и [перехват команд языковой службы прежних версий](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>См. также  
 [Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)


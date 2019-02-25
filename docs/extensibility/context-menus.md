---
title: Контекстные меню | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19838bbc1dfeeb0a0df9e1e1ce409557b6a28f1e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722383"
---
# <a name="context-menus"></a>Контекстные меню
Контекстные меню отображаются, когда пользователь щелкает правой кнопкой мыши в активную область клиентской области и очистить при отпускании правой кнопки мыши.

## <a name="editor-context-menus"></a>Контекстные меню редактора
 Перехватывая `ECMD_SHOWCONTEXTMENU`, языковой службы можно управлять контекстные меню, которые будут отображаться в редакторе. Чтобы отобразить собственное контекстное меню, обрабатывать эту команду при передаче в вашей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Если эта команда не обрабатывают, интегрированная среда разработки отображает стандартное контекстное меню, предоставленный для редактора. Также можно управлять содержимым контекстного меню на основе каждого маркера. Дополнительные сведения об этом см. в разделе [использовать текстовые метки с устаревшего API](../extensibility/using-text-markers-with-the-legacy-api.md) и [перехват команд службы прежней версией языка](../extensibility/internals/intercepting-legacy-language-service-commands.md).

## <a name="see-also"></a>См. также
- [Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)
- [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)
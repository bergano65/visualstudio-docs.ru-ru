---
title: Объект Вскодевиндовманажер | Документация Майкрософт
description: Сведения об объекте Вскодевиндовманажер, который отвечает за управление декоративными элементами, например с помощью раскрывающейся панели.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e353070c780f69ea05c1c67986f7a40f34d0659c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925851"
---
# <a name="vscodewindowmanager-object"></a>Объект Вскодевиндовманажер

Языковая служба реализует диспетчер окон кода и отвечает за управление декоративными элементами (например, с помощью раскрывающейся панели). Дополнительные сведения см. [в разделе Настройка окон кода с помощью API прежних версий](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

В следующей таблице показаны интерфейсы в `VSCodeWindowManager` объекте.

|Интерфейс|Описание|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Позволяет добавлять в окно кода декоративные элементы (такие как раскрывающиеся полосы).|